```
main_loop(cmdline_args::Vector{String}, fs::Module)
```

Set up and start a Fuse session. Use commandline arguments `cmdline_args` and the filesystem implementation defined in module `fs`.

Module `fs` must define and export all supported callback functions, the names of which are specified in `FuseLowlevelOps`.
