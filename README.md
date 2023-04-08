# Ansible Role: Configuring SSH

This role configures SSH on an Ubuntu or Arch Linux system.

**Note**: If you run this role with the defaul variables (see section "Role
Variable"), you will disable password authentication. Make sure you have a
functioning ssh key copied to the host(s) that you are running this role
against. Otherwise you might look yourself out of that system.


## Requirements

Well SSH has to be installed on the system :-).


## Role Variables

You will find the following files in a distribution specific file under
./vars/:

- sshd_config_path: the distribution specific path to the config file of the
  SSH deamon.
- sshd_name: the distribution specific name of the SSH deamon

All the following variables can be found in ./defaults/main.yml. First a list
of default configuration parameters. It might be a good idea to changed the
port that is used for SSH to something non-standard (not 22) to at least
somewhat prevent some unwanted login attempts.

- ssh_port: 22
- ssh_permit_root_login: "no"
- ssh_public_key_authentication: "yes"
- ssh_password_authentication: "no"
- ssh_permit_empty_passwords: "no"
- ssh_allow_agent_forwarding: "yes"
- ssh_x11_forwarding: "no"

The following variables are also in ./defaults/main.yml:

- sshd_enabled: true
- sshd_state: "started"
- sshd_restarted_handler_state: "started"

Set ```sshd_enabled``` to false, if you don't want the SSH service to be
enabled on the system. ```sshd_state``` is the state the SSH service will be
put in prior to configuring it, and ```sshd_restarted_handler_state``` is the
state the SSH service will be put in after the configuration.


## Dependencies

None


## Example Playbook

    - hosts: servers
      roles:
         - role: schuam.ssh_config


## License

MIT


## Author Information

This role was created in 2023 by [Andreas Schuster](https://www.schuam.de/).

