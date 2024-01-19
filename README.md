## Simple ansible playbook to setup a RHEL IdM sever with an External single level Root CA using openssl

Steps included in the playbook:

* Kickstart a VM using `virt-install` if required
* Install required packages on the VM
* Setup a Root CA using `openssl`
* Setup IPA and generate a csr
* Use the Root CA to sign the csr
* Configure IPA to import and signed CA certificate

## Usage

* Copy `hosts.in` to `hosts` and add the details (the vars should be self explaining)
* Run the playbook

        $ cd /path/to/repo
        $ ansible-playbook -i hosts idm-external-ca.yml

* Done!


## ToDo

* The cert in `/usr/share/ipa/html/ca.crt` does not get updated after import. Hence its requireed to run `ipa-certupdate` after the last step.
    * This is a known issus and is tracked in <https://bugzilla.redhat.com/show_bug.cgi?id=1549187>
