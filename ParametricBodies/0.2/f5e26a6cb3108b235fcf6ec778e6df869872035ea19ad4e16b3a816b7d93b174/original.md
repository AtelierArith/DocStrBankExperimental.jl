```
HashedLocator

- `refine<:Function`` Performs bounded Newton root-finding step
- `lims::NTuple{2,T}:` limits of the `uv` parameter
- `hash<:AbstractArray{T,2}:` Hash to supply good IC to `refine`
- `lower::SVector{2,T}:` bottom corner of the hash in ξ-space
- `step::T:` ξ-resolution of the hash
```

Type to preform efficient and fairly stable `locate`ing on parametric curves. Newton's method is fast,  but can be very unstable for general parametric curves. This is mitigated by supplying a close initial  `uv` guess by interpolating `hash``, and by bounding the derivative adjustment in the Newton`refine`ment.

---

```
HashedLocator(curve,lims;t⁰=0,step=1,buffer=2,T=Float32,mem=Array)
```

Creates HashedLocator by sampling the curve and finding the bounding box. This box is expanded by the amount `buffer`.  The hash array is allocated to span the box with resolution `step` and initialized using `update!(::,curve,t⁰,samples)`.

Example:

```
t = 0.
curve(θ,t) = SA[cos(θ+t),sin(θ+t)]
locator = HashedLocator(curve,(0.,2π),t⁰=t,step=0.25)
@test isapprox(locator(SA[.3,.4],t),atan(4,3),rtol=1e-4)
@test isapprox(curve(locator(SA[-1.2,.9],t),t),SA[-4/5,3/5],rtol=1e-4)

body = ParametricBody(curve,locator)
@test isapprox(sdf(body,SA[-.3,-.4],t),-0.5,rtol=1e-4) # inside hash
@test isapprox(sdf(body,SA[-3.,-4.],t), 4.0,rtol=2e-2) # outside hash
```
