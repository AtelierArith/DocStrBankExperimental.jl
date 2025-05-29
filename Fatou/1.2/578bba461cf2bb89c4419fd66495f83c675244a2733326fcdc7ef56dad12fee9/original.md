```
juliafill(::Expr;                     # primary map, (z, c) -> F
  Q::Expr     = :(abs2(z)),           # escape criterion, (z, c) -> Q
  C::Expr     = :((angle(z)/(2π))*n^p)# coloring, (z, n=iter., p=exp.) -> C
  ∂    = π/2, # Array{Float64,1}      # Bounds, [x(a),x(b),y(a),y(b)]
  n::Integer  = 176,                  # horizontal grid points
  N::Integer  = 35,                   # max. iterations
  ϵ::Number   = 4,                    # basin ϵ-Limit criterion
  iter::Bool  = false,                # toggle iteration mode
  p::Number   = 0,                    # iteration color exponent
  x0          = nothing,              # orbit starting point
  orbit::Int  = 0,                    # orbit cobweb depth
  depth::Int  = 1,                    # depth of function composition
  cmap::String= "",                   # imshow color map
  plane::Bool = false,                # convert input disk to half-plane
  disk::Bool  = false)                # convert output half-plane to disk
```

`Define` filled Julia basin in `Fatou`

# Exmaples

```Julia
julia> juliafill("z^2-0.06+0.67im",∂=[-1.5,1.5,-1,1],N=80,n=1501,cmap="RdGy")
```
