```
NLLSsolver.computeresidual(mycost, vars...)
```

Compute the residuals generated by `mycost` given the variables `vars`. The return value must be a vector.

# Example

For the Rosenbrock problem with

```julia
struct Rosenbrock <: NLLSsolver.AbstractResidual
    a::Float64
    b::Float64
end
```

the user should define the following function:

```julia
NLLSsolver.computeresidual(res::Rosenbrock, x, y) = SVector(res.a * (1 - x), res.b * (x ^ 2 - y))
```

!!! tip
    If the residual length is known at compile time, return a static vector.


!!! note
    Required user-specialized API function.

