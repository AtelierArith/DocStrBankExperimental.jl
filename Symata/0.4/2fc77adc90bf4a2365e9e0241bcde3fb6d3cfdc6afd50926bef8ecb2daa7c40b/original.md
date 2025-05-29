```
debugmxpr(s::String)
```

parse and evaluate `s` as a Symata expression. From Julia, this prints the stack trace when an error is raised. If the same expression entered at the Symata command line, the stack trace will not be printed.
