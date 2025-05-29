```
@butensor tensor_expr
```

Use Bumper.jl to handle allocation of temporary tensors. This macro will use the default buffer and automatically reset it after the tensor expression has been evaluated. This macro is equivalent to `@no_escape @tensor tensor_expr` with all temporary allocations handled by Bumper.jl.

!!! note
    This macro requires Bumper.jl to be installed and loaded. This can be achieved by running `using Bumper` or `import Bumper` before using the macro.

