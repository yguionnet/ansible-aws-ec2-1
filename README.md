# ansible-aws-ec2
Changes from @yguionnet:

* add ask-pass in ansible.cfg

  [privilege_escalation]
  become_ask_pass= true

* change subnet in group_vars for an existing one

* add environment section at playbook top level:
  environment:
    AWS_ACCESS_KEY: "{{ my_access_key }}"
    AWS_SECRET_KEY: "{{ my_secret_key }}"
    AWS_EC2_REGION: "{{ my_region }}"
   
  then you must create a yaml file outside repository for safety:
  secret_vars.yml
    my_access_key: [Access Key]
    my_secret_key: [Secret Key]
    my_region: us-east-1

  then launch the playbook as follow:
  ansible-playbook -e @../secret-vars.yml deploy.yml
