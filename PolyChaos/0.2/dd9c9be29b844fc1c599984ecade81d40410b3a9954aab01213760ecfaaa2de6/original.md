```
integrate(f::Function,nodes::AbstractVector{<:Real},weights::AbstractVector{<:Real})
integrate(f::Function,q::AbstractQuad)
integrate(f::Function,opq::AbstractOrthoPoly)
```

integrate function `f` using quadrature rule specified via `nodes`, `weights`. For example $\int_0^1 6x^5 = 1$ can be solved as follows:

```@repl
julia> opq = Uniform01OrthoPoly(3) # a quadrature rule is added by default

julia> integrate(x -> 6x^5, opq)
0.9999999999999993
```

!!! note



  * function $f$ is assumed to return a scalar.
  * interval of integration is "hidden" in `nodes`.
