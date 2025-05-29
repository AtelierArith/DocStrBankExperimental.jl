```
runexpr(expr::AbstractString)
```

Ask the server to run julia code in a string pass as parameters.

# Parameters

  * expr: Julia code to run in the server.

# Optionals

  * port: Port (default=3000).
  * output: stream in which it is shown the output of the run.
