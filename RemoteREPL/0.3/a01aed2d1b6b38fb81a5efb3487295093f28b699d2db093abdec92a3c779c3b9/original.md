```
connect_remote([host=localhost,] port::Integer=27754;
             tunnel = (host != localhost) ? :ssh : :none,
             ssh_opts = ``, session_id = nothing)
```

Connect to remote server without any REPL integrations. This will allow you to use `@remote`, but not the REPL mode. Useful in circumstances where no REPL is available, but interactivity is desired like Jupyter or Pluto notebooks. Otherwise, see `connect_repl`.
