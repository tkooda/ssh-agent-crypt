ssh-agent-crypt
=====================

Use RSA SSH keys from ssh-agent to store / retreive encrypted (e.g. config) data


NOTES:
------
 - this only works with RSA (and not DSA/ECDSA) keys because RSA keys are the only ones that produce a consistent signature output (given a consistent input) that can be used for encryption/decryption
 - 'set' reads from stdin
 - 'get' writes to stdout
 - order and case are significant for identifiers
 - obtain SSH key md5 fingerprints with:  `ssh-agent-crypt -l`
 - use openssl compatible method of encryption/decryption


EXAMPLE USAGE:
--------------
```
   ## view all SSH keys available in the ssh-agent
   ssh-agent-crypt -l

   ## store an encrypted configuration setting using all available usable RSA SSH keys in the ssh-agent
   echo 'myPassword123' | ssh-agent-crypt  --all  set  imaps myusername example.com

   ## retreive an encrypted configuration setting (using the first usable RSA SSH keys in the ssh-agent)
   ssh-agent-crypt  get  imaps myusername example.com
```
