```
send_command(pstdin::Base.Pipe, pstdout::Base.Pipe, cmd::String; is_done=nested_parens_match, timeout=Inf, line_ending='
```

')

Open a solver in a new process with in, out, and err pipes. Uses Base.process. Check the source code to see the exact implementation.
