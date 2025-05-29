```
connect_repl([host=localhost,] port::Integer=27754;
             tunnel = (host != localhost) ? :ssh : :none,
             ssh_opts = ``, region=nothing, namespace=nothing,
             repl=Base.active_repl, session_id = nothing)
```

Connect client REPL to a remote `host` on `port`. This is then accessible as a remote sub-repl of the current Julia session.

For security, `connect_repl()` uses an ssh tunnel for remote hosts. This means that `host` needs to be running an ssh server and you need ssh credentials set up for use on that host. For secure networks this can be disabled by setting `tunnel=:none`.

To provide extra options to SSH, you may pass a `Cmd` object in the `ssh_opts` keyword, for example an identity file may be set with ```ssh_opts = `-i /path/to/identity.pem` ```. For a more permanent solution, add a `Host` section to your ssh config file.

You can also use the following technologies for tunneling in place of SSH:

1. AWS Session Manager: set `tunnel=:aws`. The optional `region` keyword argument can be used to specify the AWS Region of your server.
2. kubectl: set `tunnel=:k8s`. The optional `namespace` keyword argument can be used to specify the namespace of your Kubernetes resource.

See README.md for more information.
