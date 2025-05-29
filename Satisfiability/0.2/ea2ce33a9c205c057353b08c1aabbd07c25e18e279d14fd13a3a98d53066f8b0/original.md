```
save(z1, z2,..., io=open("out.smt", "w"))
save(z1, z2,..., io=open("out.smt", "w", line_ending='
```

', start*commands=nothing, end*commands=nothing)

Write the SMT representation of `z` or `and(z1,...,zn)` to an IO object. Keyword arguments:

  * `io` is a Julia IO object, for example an open file for writing.
  * `line_ending` configures the line ending character. If left off, the default is `

`on Windows systems and` ` everywhere else.

  * `start_commands` are inserted before `smt(z)`. Typically one uses this to include `(set-info ...)` or `(set-option ...)` statements.
  * `end_commands` are inserted after `(check-sat)`. This tends to be less useful unless you already know whether your problem is satisfiable.
