```
add_preamble!(pre::AbstractString...; reset=false)
```

Adds preamble statements on top of the default preamble. `pre` is any number of `AbstractString`s.

If you already have a number of preamble statements and you would like to get rid of them first before adding new statements, pass `reset=true`.
