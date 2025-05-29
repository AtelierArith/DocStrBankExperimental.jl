```
jacview(sess::PyObject, f::Function, θ::Union{Array{Float64}, PyObject, Missing}, 
u0::Array{Float64}, args...)
```

Performs gradient test for a vector function. `f` has the signature 

```
f(θ, u) -> r, J
```

Here `θ` is a nuisance  parameter, `u` is the state variables (w.r.t. which the Jacobian is computed), `r` is the residual vector, and `J` is the Jacobian matrix (a dense matrix or a [`SparseTensor`](@ref)).

# Example 1

```julia
u0 = rand(10)
function verify_jacobian_f(θ, u)
    r = u^3+u - u0
    r, spdiag(3u^2+1.0)
end
jacview(sess, verify_jacobian_f, missing, u0)
```

# Example 2

```
u0 = rand(10)
rs = rand(10)
function verify_jacobian_f(θ, u)
    r = [u^2;u] - [rs;rs]
    r, [spdiag(2*u); spdiag(10)]
end
jacview(sess, verify_jacobian_f, missing, u0); close("all")
```
