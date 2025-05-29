```
Spherical(r, θ, ϕ)
```

3D spherical coordinates

There are many Spherical coordinate conventions and this library uses a somewhat exotic one. Given a vector `v` with Cartesian coordinates `xyz`, let `v_xy = [x,y,0]` be the orthogonal projection of `v` on the `xy` plane.

  * `r` is the radius. It is given by `norm(v, 2)`.
  * `θ` is the azimuth. It is the angle from the x-axis to `v_xy`
  * `ϕ` is the latitude. It is the angle from `v_xy` to `v`.

```jldoctest
julia> v = randn(3);

julia> sph = SphericalFromCartesian()(v);

julia> r = sph.r; θ = sph.θ; ϕ = sph.ϕ;

julia> v ≈ [r * cos(θ) * cos(ϕ), r * sin(θ) * cos(ϕ), r * sin(ϕ)]
true
```
