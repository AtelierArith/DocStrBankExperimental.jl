```
test_hessian(f::Function, x0::Array{Float64, 1}; scale::Float64 = 1.0)
```

Testing the Hessian of a scalar function `f`: `g, H = f(x)` where `y` is a scalar output, `g` is a vector gradient output, and `H` is the Hessian.
