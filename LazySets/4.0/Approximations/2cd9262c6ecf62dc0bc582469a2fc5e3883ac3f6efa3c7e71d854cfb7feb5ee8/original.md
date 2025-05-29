```
PolarDirections{N<:AbstractFloat, VN<:AbstractVector{N}} <: AbstractDirections{N, VN}
```

Polar directions representation.

### Fields

  * `Nφ`    – length of the partition of the polar angle
  * `stack` – list of computed directions

### Notes

The `PolarDirections` constructor computes a sample of the unit sphere in $ℝ^2$, which is parameterized by the polar angle $φ ∈ Dφ := [0, 2π]$; see the Wikipedia entry on the [polar coordinate system](https://en.wikipedia.org/wiki/Polar_coordinate_system) for details. The resulting directions are stored in `stack`.

The integer argument $Nφ$ defines how many samples of $Dφ$ are taken. The Cartesian components of each direction are obtained with

$$
[cos(φᵢ), sin(φᵢ)].
$$

### Examples

The integer passed as an argument is used to discretize $φ$:

```jldoctest; filter = r"2246[0-9]*e-16"
julia> pd = PolarDirections(2);

julia> pd.stack
2-element Vector{Vector{Float64}}:
 [1.0, 0.0]
 [-1.0, 1.2246467991473532e-16]

julia> length(pd)
2
```
