```
sigt, lastpc = signature([interp::Interpreter=RecursiveInterpreter()], frame::Frame, pc::Int)
```

Compute the signature-type `sigt` of a method whose definition in `frame` starts at `pc`. Generally, `pc` should point to the `Expr(:method, methname)` statement, in which case `lastpc` is the final statement number in `frame` that is part of the signature (i.e, the line above the 3-argument `:method` expression). Alternatively, `pc` can point to the 3-argument `:method` expression, as long as all the relevant SSAValues have been assigned. In this case, `lastpc == pc`.

If no 3-argument `:method` expression is found, `sigt` will be `nothing`.
