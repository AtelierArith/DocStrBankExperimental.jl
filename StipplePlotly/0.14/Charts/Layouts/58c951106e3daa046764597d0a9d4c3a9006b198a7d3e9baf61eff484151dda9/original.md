```
  GeoProjection()
```

---

# Examples

---

```
julia>
```

---

# Properties

---

  * `distance::Float64` - For satellite projection type only. Sets the distance from the center of the sphere to the point of view as a proportion of the sphere’s radius.  Type: number greater than or equal to `1.001` | Default: `2`
  * `parallels::Vector{Float64}` - For conic projection types only. Sets the parallels (tangent, secant) where the cone intersects the sphere.
  * `rotation::Protation` - Check Protation struct for more details
  * `scale::Float64` - Zooms in or out on the map view. A scale of "1" corresponds to the largest zoom level that fits the map's lon and lat ranges. number greater than or equal to `0` | Default: `1`
  * `tilt::Float64` - For satellite projection type only. Sets the tilt angle of perspective projection. Type: `number` | Default: `0`
  * `type::String` - Sets the projection type. Type: enumerated , one of ( `"albers"` | `"albers usa"` | `"azimuthal equal area"` | `"azimuthal equidistant"` | `"conic equal area"` | `"conic conformal"` | `"conic equidistant"` | `"equidistant conic"` | `"gnomonic"` | `"mercator"` | `"natural earth"` | `"orthographic"` | `"stereographic"` | `"transverse mercator"` )
