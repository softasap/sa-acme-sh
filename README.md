sa-acme-sh
==========

[![Build Status](https://travis-ci.com/softasap/sa-acme-sh.svg?branch=master)](https://travis-ci.com/softasap/sa-acme-sh)


Example of usage:

Simple

```YAML

     - {
         role: "sa-acme-sh",
         option_setup_cron: true
       }


```

Advanced

```YAML

vars:

  my_le_config_properties: 
    - {regexp: "^export GD_Key=*", line: "export GD_Key=OHOH"}
    - {regexp: "^export GD_Secret=*", line: "export GD_Secret=AHAH"} 

  roles:
    - {
        role: "sa-acme-sh",

        option_setup_cron: true,

        le_wellknown_path: "/var/www/.well-known/acme-challenge",
        acmesh_version: 2.8.0,
        le_config_properties: "{{ my_le_config_properties }}" 
      }


```

Issuing certificate example:

Certificate issuing via godaddy provider 

```sh

export GD_Key=***
export GD_Secret=***
acme.sh --issue -d voronenko.net -d www.voronenko.net --dns dns_gd

```

Listing certificates 
```
acme.sh --list
Main_Domain    KeyLength  SAN_Domains        Created                       Renew
voronenko.net  ""         www.voronenko.net  Wed Mar  6 12:37:30 UTC 2019  Sun May  5 12:37:30 UTC 2019
```



Usage with ansible galaxy workflow
----------------------------------

If you installed the `sa-acme-sh` role using the command


`
   ansible-galaxy install softasap.sa-acme-sh
`

the role will be available in the folder `library/softasap.sa-acme-sh`
Please adjust the path accordingly.

```YAML

     - {
         role: "softasap.sa-acme-sh"
       }

```




Copyright and license
---------------------

Code is dual licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) and the [MIT License] (http://opensource.org/licenses/MIT). Choose the one that suits you best.

Reach us:

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)

Join gitter discussion channel at [Gitter](https://gitter.im/softasap)

Discover other roles at  http://www.softasap.com/roles/registry_generated.html

visit our blog at http://www.softasap.com/blog/archive.html 
