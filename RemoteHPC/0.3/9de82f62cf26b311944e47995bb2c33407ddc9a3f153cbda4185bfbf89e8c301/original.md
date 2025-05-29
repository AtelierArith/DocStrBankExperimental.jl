```
Server(name                ::String,
       username            ::String,
       domain              ::String,
       scheduler           ::Scheduler,
       julia_exec          ::String,
       jobdir              ::String,
       max_concurrent_jobs ::Int)
Server(name::String)
```

A [`Server`](@ref) represents a daemon running either locally or on some remote cluster. It facilitates all remote operations that are required to save, submit, monitor and retrieve HPC jobs.

As with any [`Storable`](@ref), `name` is used simply as a label.

`username` and `domain` should be those that allow for `ssh` connections between your local machine and the remote host. Make sure that passwords are not required to execute `ssh` commands, i.e. by having copied your `ssh` keys using `ssh-copy-id`. 

`julia_exec` should be the path on the remote host where to find the `julia` executable. `scheduler` will be automatically deduced but can be overridden if needed.
