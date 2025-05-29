```
rk4(y::Union{PyObject, Float64, Array{Float64}}, T::Union{PyObject, Float64}, 
            NT::Union{PyObject,Int64}, f::Function, θ::Union{PyObject, Missing}=missing)
```

次の方程式を解きます 

$$
\frac{dy}{dt} = f(y, t, \theta)
$$

ルンゲ・クッタ（4次）法を用いて。
