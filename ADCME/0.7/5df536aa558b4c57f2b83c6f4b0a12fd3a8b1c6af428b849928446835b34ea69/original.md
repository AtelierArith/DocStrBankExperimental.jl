```
test_jacobian(f::Function, x0::Array{Float64, 1}; scale::Float64 = 1.0, showfig::Bool = true)
```

Testing the gradients of a vector function `f`: `y, J = f(x)` where `y` is a vector output and `J` is the Jacobian.
