```
test_gradients(f::Function, x0::Array{Float64, 1}; scale::Float64 = 1.0, showfig::Bool = true)
```

Testing the gradients of a vector function `f`: `y, J = f(x)` where `y` is a scalar output and `J` is the vector gradient.
