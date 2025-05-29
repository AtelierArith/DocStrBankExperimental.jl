```
setop!(model; uop=nothing, yop=nothing, dop=nothing, xop=nothing, fop=nothing) -> model
```

Set the operating points of `model` (both [`LinModel`](@ref) and [`NonLinModel`](@ref)).

Introducing deviations vectors around manipulated input `uop`, model output `yop`, measured disturbance `dop`, and model state `xop` operating points (a.k.a. nominal values):

$$
\begin{align*}
    \mathbf{u_0}(k) &= \mathbf{u}(k) - \mathbf{u_{op}} \\
    \mathbf{d_0}(k) &= \mathbf{d}(k) - \mathbf{d_{op}} \\
    \mathbf{y_0}(k) &= \mathbf{y}(k) - \mathbf{y_{op}} \\
    \mathbf{x_0}(k) &= \mathbf{x}(k) - \mathbf{x_{op}} \\
\end{align*}
$$

The state-space description of [`LinModel`](@ref) around the operating points is:

$$
\begin{aligned}
    \mathbf{x_0}(k+1) &= \mathbf{A x_0}(k) + \mathbf{B_u u_0}(k) + \mathbf{B_d d_0}(k) 
                         + \mathbf{f_{op}}   - \mathbf{x_{op}}                                              \\
    \mathbf{y_0}(k)   &= \mathbf{C x_0}(k) + \mathbf{D_d d_0}(k) 
\end{aligned}
$$

and, for [`NonLinModel`](@ref):

$$
\begin{aligned}
    \mathbf{x_0}(k+1) &= \mathbf{f}\Big(\mathbf{x_0}(k), \mathbf{u_0}(k), \mathbf{d_0}(k), \mathbf{p}\Big) 
                            + \mathbf{f_{op}} - \mathbf{x_{op}}                                             \\
    \mathbf{y_0}(k)   &= \mathbf{h}\Big(\mathbf{x_0}(k), \mathbf{d_0}(k), \mathbf{p}\Big)
\end{aligned}
$$

The state `xop` and the additional `fop` operating points are frequently zero e.g.: when  `model` comes from system identification. The two vectors are internally used by [`linearize`](@ref) for non-equilibrium points.

# Examples

```jldoctest
julia> model = setop!(LinModel(tf(3, [10, 1]), 2.0), uop=[50], yop=[20])
LinModel with a sample time Ts = 2.0 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d

julia> y = model()
1-element Vector{Float64}:
 20.0
```
