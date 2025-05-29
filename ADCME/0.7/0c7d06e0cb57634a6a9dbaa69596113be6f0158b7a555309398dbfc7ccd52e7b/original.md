```
newton_raphson_with_grad(f::Function, 
u0::Union{Array,PyObject}, 
θ::Union{Missing,PyObject, Array{<:Real}}=missing,
args::PyObject...) where T<:Real
```

Differentiable Newton-Raphson algorithm. See [`newton_raphson`](@ref).

Use `ADCME.options.newton_raphson` to supply options. 

# Example

```julia
function f(θ, x)
    x^3 - θ, 3spdiag(x^2)
end

θ = constant([2. .^3;3. ^3; 4. ^3])
x = newton_raphson_with_grad(f, constant(ones(3)), θ)
run(sess, x)≈[2.;3.;4.]
run(sess, gradients(sum(x), θ))
```
