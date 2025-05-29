```
linearize(model::SimModel; x=model.x0+model.xop, u=model.uop, d=model.dop) -> linmodel
```

Linearize `model` at the operating points `x`, `u`, `d` and return the [`LinModel`](@ref).

The arguments `x`, `u` and `d` are the linearization points for the state $\mathbf{x}$, manipulated input $\mathbf{u}$ and measured disturbance $\mathbf{d}$, respectively (not necessarily an equilibrium, details in Extended Help). By default, [`ForwardDiff`](@extref ForwardDiff) automatically computes the Jacobians of $\mathbf{f}$ and $\mathbf{h}$ functions. Modify the `jacobian` keyword argument at the construction of `model` to swap the backend.

!!! warning
    See Extended Help if you get an error like:     `MethodError: no method matching (::var"##")(::Vector{ForwardDiff.Dual})`.


# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->x.^3 + u, (x,_,_)->x, 0.1, 1, 1, 1, solver=nothing);

julia> linmodel = linearize(model, x=[10.0], u=[0.0]); 

julia> linmodel.A
1×1 Matrix{Float64}:
 300.0
```

# Extended Help

!!! details "Extended Help"
    With the nonlinear state-space model:

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &= \mathbf{f}\Big(\mathbf{x}(k), \mathbf{u}(k), \mathbf{d}(k), \mathbf{p}\Big)  \\
        \mathbf{y}(k)   &= \mathbf{h}\Big(\mathbf{x}(k), \mathbf{d}(k), \mathbf{p}\Big)
    \end{aligned}
    $$

    its linearization at the operating point $\mathbf{x_{op}, u_{op}, d_{op}}$ is:

    $$
    \begin{aligned}
        \mathbf{x_0}(k+1) &≈ \mathbf{A x_0}(k) + \mathbf{B_u u_0}(k) + \mathbf{B_d d_0}(k)  
                            + \mathbf{f(x_{op}, u_{op}, d_{op}, p)} - \mathbf{x_{op}}         \\
        \mathbf{y_0}(k)   &≈ \mathbf{C x_0}(k) + \mathbf{D_d d_0}(k) 
    \end{aligned}
    $$

    based on the deviation vectors $\mathbf{x_0, u_0, d_0, y_0}$ introduced in [`setop!`](@ref) documentation, and the Jacobian matrices:

    $$
    \begin{aligned}
        \mathbf{A}   &= \left. \frac{∂\mathbf{f(x, u, d, p)}}{∂\mathbf{x}} \right|_{\mathbf{x=x_{op},\, u=u_{op},\, d=d_{op}}} \\
        \mathbf{B_u} &= \left. \frac{∂\mathbf{f(x, u, d, p)}}{∂\mathbf{u}} \right|_{\mathbf{x=x_{op},\, u=u_{op},\, d=d_{op}}} \\
        \mathbf{B_d} &= \left. \frac{∂\mathbf{f(x, u, d, p)}}{∂\mathbf{d}} \right|_{\mathbf{x=x_{op},\, u=u_{op},\, d=d_{op}}} \\
        \mathbf{C}   &= \left. \frac{∂\mathbf{h(x, d, p)}}{∂\mathbf{x}}    \right|_{\mathbf{x=x_{op},\, d=d_{op}}}             \\
        \mathbf{D_d} &= \left. \frac{∂\mathbf{h(x, d, p)}}{∂\mathbf{d}}    \right|_{\mathbf{x=x_{op},\, d=d_{op}}}
    \end{aligned}
    $$

    Following [`setop!`](@ref) notation, we find:

    $$
    \begin{aligned}
        \mathbf{f_{op}} &= \mathbf{f(x_{op}, u_{op}, d_{op}, p)} \\
        \mathbf{y_{op}} &= \mathbf{h(x_{op}, d_{op}, p)}
    \end{aligned}
    $$

    Notice that $\mathbf{f_{op} - x_{op} = 0}$ if the point is an equilibrium. The  equations are similar if the nonlinear model has nonzero operating points.

    Automatic differentiation (AD) allows exact Jacobians. The [`NonLinModel`](@ref) `f` and `h` functions must be compatible with this feature though. See [`JuMP` documentation](@extref JuMP Common-mistakes-when-writing-a-user-defined-operator) for common mistakes when writing these functions.

