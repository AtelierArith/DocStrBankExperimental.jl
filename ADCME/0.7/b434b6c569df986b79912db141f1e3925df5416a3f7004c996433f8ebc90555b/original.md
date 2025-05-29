```
NonlinearConstrainedProblem(f::Function, L::Function, θ::PyObject, u0::Union{PyObject, Array{Float64}}; options::Union{Dict{String, T}, Missing}=missing) where T<:Integer
```

Computes the gradients $\frac{\partial L}{\partial \theta}$

$$
\min \ L(u) \quad \mathrm{s.t.} \ F(\theta, u) = 0
$$

`u0` is the initial guess for the numerical solution `u`, see [`newton_raphson`](@ref).

Caveats: Assume `r, A = f(θ, u)` and `θ` are the unknown parameters, `gradients(r, θ)` must be defined (backprop works properly)

Returns: It returns a tuple (`L`: loss, `C`: constraints, and `Graidents`)

$$
\left(L(u), u, \frac{\partial L}{\partial θ}\right)
$$

# Example

We want to solve the following constrained optimization problem  $\begin{aligned}\min_\theta &\; L(u) = (u-1)^3\\ \text{s.t.} &\; u^3 + u = \theta\end{aligned}$ The solution is $\theta = 2$. The Julia code is 

```julia
function f(θ, u)
    u^3 + u - θ, spdiag(3u^2+1) 
end
function L(u) 
    sum((u-1)^2)
end
pl = Variable(ones(1))
l, θ, dldθ = NonlinearConstrainedProblem(f, L, pl, ones(1))
```

We can coupled it with a mathematical optimizer 

```julia
using Optim 
sess = Session(); init(sess)
BFGS!(sess, l, dldθ, pl) 
```
