```
 save(path::String)
```

Create a phony [`Gnuplot`](@ref) instance, without the underlying process attached. Instead, write messages to file. You can then later turn the file into a plot by running it with Gnuplot from the command line, or run a `pipeline` from Julia.
