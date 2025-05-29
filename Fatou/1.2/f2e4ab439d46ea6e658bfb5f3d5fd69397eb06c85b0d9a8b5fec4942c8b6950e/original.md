```
newton(::Expr;                        # primary map, (z, c) -> F
  C::Expr     = :((angle(z)/(2π))*n^p)# coloring, (z, n=iter., p=exp.) -> C
  ∂    = π/2, # Array{Float64,1}      # Bounds, [x(a),x(b),y(a),y(b)]
  n::Integer  = 176,                  # horizontal grid points
  N::Integer  = 35,                   # max. iterations
  ϵ::Number   = 4,                    # basin ϵ-Limit criterion
  iter::Bool  = false,                # toggle iteration mode
  p::Number   = 0,                    # iteration color exponent
  m::Number   = 0,                    # Newton multiplicity factor
  mandel::Bool= false,                # toggle Mandelbrot mode
  seed::Number= 0.0+0.0im,            # Mandelbrot seed value
  x0          = nothing,              # orbit starting point
  orbit::Int  = 0,                    # orbit cobweb depth
  depth::Int  = 1,                    # depth of function composition
  cmap::String= "",                   # imshow color map
  plane::Bool = false,                # convert input disk to half-plane
  disk::Bool  = false)                # convert output half-plane to disk
```

`Define` Newton basin in `Fatou`

# Examples

```Julia
julia> newton("z^3-1",n=800,cmap="brg")
```
