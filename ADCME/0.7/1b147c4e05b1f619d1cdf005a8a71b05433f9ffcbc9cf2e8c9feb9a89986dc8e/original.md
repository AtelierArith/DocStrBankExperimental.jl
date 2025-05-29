```
rk4(y::Union{PyObject, Float64, Array{Float64}}, T::Union{PyObject, Float64}, 
            NT::Union{PyObject,Int64}, f::Function, θ::Union{PyObject, Missing}=missing)
```

Solves 

$$
\frac{dy}{dt} = f(y, t, \theta)
$$

with Runge-Kutta (order 4) method. 
