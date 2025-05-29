```
Optimizer(problem, solver)
```

Constructs an `Optimizer` for the given `problem` using the specificed `solver` backend.

Supported backends are:

  * [`QPSolver`](@ref)
  * [`NLPSolver`](@ref)
  * [`MCPSolver`](@ref)

Please consult their documentation for further information.

# Example

```@example running_example
solver = QPSolver()
optimizer = Optimizer(problem, solver)
```
