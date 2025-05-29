```
@implement_gradient(f, f_dfdx)
```

This macro allows specifying a function `f_dfdx` that provides an analytical  derivative of the function `f`, and is invoked when `f` is differentiated  using automatic differentiation based on `ForwardDiff.jl` (e.g. when using `Tensors.jl`'s  [`gradient`](@ref) or [`hessian`](@ref)), or one of `ForwardDiff.jl`'s API). The function `f_dfdx` must take the same argument as `f` and should return both the value of `f` and  the gradient, i.e. `fval, dfdx_val = f_dfdx(x)`. The following combinations of input and output types are supported:

| `x`                 | `f(x)`              | `dfdx`              |
|:------------------- |:------------------- |:------------------- |
| `Number`            | `Number`            | `Number`            |
| `Number`            | `Vec`               | `Vec`               |
| `Number`            | `SecondOrderTensor` | `SecondOrderTensor` |
| `Vec`               | `Number`            | `Vec`               |
| `Vec`               | `Vec`               | `Tensor{2}`         |
| `SecondOrderTensor` | `Number`            | `SecondOrderTensor` |
| `SecondOrderTensor` | `SecondOrderTensor` | `FourthOrderTensor` |

Note that if one tensor if of symmetric type, then all tensors must  be of symmetric type
