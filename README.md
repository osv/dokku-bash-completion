dokku-bash-completion
=====================

Bash completion for dokku and dokku-alt. Also it may create command for ssh-ing remote that complete too.

## Installing
```shell
git clone https://github.com/osv/dokku-bash-completion.git /var/lib/dokku/plugins/dokku-bash-completion
dokku plugins-install
```

## For remote

```shell
ssh dokku@example.com completion dokku-cli | sudo bash
# If you want force domain when example.com machine
# have different hostname than example.com:
ssh dokku@example.com completion dokku-cli example.com | sudo bash
```

The "/usr/local/bin/dokku-cli" will be created or update
(but only if that command created before by ssh ... completion dokku-cli) and looks like:

```shell
#!/usr/bin/env bash
# autogenerated by ssh dokku@example.com completion haruko-cli
# -- DOKKU_COMPLETION_CLI --

ssh -t dokku@example.com $@ 2>/dev/null
```

Other file "/etc/bash_completion.d/dokku-cli" created for completion.

Some caching used, but still, completion may be slow on high ping :).

Currently can complete:
- commands
- application ("<app>")
- env variables for (config:get, config:set, etc)

## TODO

- dokku-alt - complete database name
- complete volume names (volume:list)