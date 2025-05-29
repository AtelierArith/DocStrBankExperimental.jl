```
SphericalDirections{N<:AbstractFloat, VN<:AbstractVector{N}} <: AbstractDirections{N, VN}
```

Spherical directions representation.

### Fields

  * `Nθ`    – length of the partition of the azimuthal angle
  * `Nφ`    – length of the partition of the polar angle
  * `stack` – list of computed directions

### Notes

The `SphericalDirections` constructor provides a sample of the unit sphere in $ℝ^3$, which is parameterized by the azimuthal and polar angles $θ ∈ Dθ := [0, π]$ and $φ ∈ Dφ := [0, 2π]$ respectively; see the Wikipedia entry on the [spherical coordinate system](https://en.wikipedia.org/wiki/Spherical_coordinate_system) for details.

The integer arguments $Nθ$ and $Nφ$ define how many samples along the domains $Dθ$ and $Dφ$ are respectively taken. The Cartesian components of each direction are obtained with

$$
[sin(θᵢ)*cos(φᵢ), sin(θᵢ)*sin(φᵢ), cos(θᵢ)].
$$

The north and south poles are treated separately so that those points are not considered more than once.

### Examples

The template can be built in different ways. If you pass only one integer, the same value is used to discretize both $θ$ and $φ$:

```jldoctest spherical_directions; filter = r"1232[0-9]*e-17.*2246[0-9]*e-16.*1232[0-9]*e-17"
julia> sd = SphericalDirections(3);

julia> sd.Nθ, sd.Nφ
(3, 3)

julia> length(sd)
4
```

Pass two integers to control the discretization in $θ$ and in $φ$ separately:

```jldoctest spherical_directions
julia> sd = SphericalDirections(4, 5);

julia> length(sd)
10

julia> sd = SphericalDirections(4, 8);

julia> length(sd)
16
```
