```
fame(io, command::String)
fame(command::String; quiet=false)
```

Run the FAME command `command` and write the output to `io` or the screen. If `io` is not specified the output can be suppressed with `quiet=true`.
