```
NonRecursiveInterpreter <: Interpreter
```

`NonRecursiveInterpreter` is an [`Interpreter`](@ref) that evaluates any `:call` expressions in the code being interpreted using Julia's normal code execution engine with the native compiler.

`JuliaInterpreter.Compiled` is aliased to `NonRecursiveInterpreter` for backward compatibility.
