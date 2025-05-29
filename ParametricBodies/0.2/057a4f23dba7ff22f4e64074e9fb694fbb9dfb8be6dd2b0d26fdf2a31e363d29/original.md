```
ParametricBody{T::Real}(curve,locate) <: AbstractBody

- `curve(u,t)` parametrically defined curve
- `dotS(u,t)=derivative(t->curve(u,t),t)` time derivative of curve 
- `locate(ξ,t)` method to find nearest parameter `u` to `ξ`
- `map(x,t)=x` mapping from `x` to `ξ`
- `scale=|∇map|⁻¹` distance scaling from `ξ` to `x`
- `thk=0` thickness offset for the signed distance
- `boundary=true` if the curve represent a body boundary, not a space-curve
```

Explicitly defines a geometry by an unsteady parametric curve. The curve is currently limited  to be univariate, and must wind counter-clockwise if closed. The optional `dotS`, `map`, `scale`,  `thk` and `boundary` parameters allow for more general geometry embeddings.

Example:

```
curve(θ,t) = SA[cos(θ+t),sin(θ+t)]
locate(x::SVector{2},t) = atan(x[2],x[1])-t
body = ParametricBody(curve,locate)

@test body.curve(body.locate(SA[4.,3.],1),1) == SA[4/5,3/5]

d,n,V = measure(body,SA[-.75,1],4.)
@test d ≈ 0.25
@test n ≈ SA[-3/5, 4/5]
@test V ≈ SA[-4/5,-3/5]
```
