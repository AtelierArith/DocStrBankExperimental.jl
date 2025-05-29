```
sphericaltocartesian(ρ, θ, ϕ)
```

Return `Point3D(x, y, z)` corresponding to `(ρ, θ, ϕ)`:

  * ρ is the distance from the origin (ie radius)
  * θ is the azimuthal angle (the longitude) 0 is +x, π is -x, 2π is +x
  * ϕ is the polar angle (the colatitude) 0 is North Pole, π is South Pole

There are two major conventions for spherical coordinate notation.

In physics books:

(ρ, θ, φ) gives the radial distance, polar angle (colatitude), and azimuthal angle (longitude)

In mathematics books:

(ρ, θ , φ ) gives the radial distance, azimuthal angle (longitude), and polar angle (colatitude)

So we're using the mathematics one here.
