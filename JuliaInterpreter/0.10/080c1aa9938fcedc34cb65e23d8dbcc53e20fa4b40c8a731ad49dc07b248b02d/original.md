```
RecursiveInterpreter <: Interpreter
```

`RecursiveInterpreter` is an [`Interpreter`](@ref) that recursively interprets any `:call` expressions in the code being interpreted.

With this interpreter, code runs in fully interpreted mode; it will never be compiled for execution.
