```
mutable struct Pos{T} where T<:Real
```

Type with fields:

  * `.Na::Int`: grid index of last leading point
  * `.Nlctp::Int`: grid index of lower classical turning point
  * `.Nmin::Int`: grid index of (screened) potential minimum
  * `.Nuctp::Int`: grid index of upper classical turning point
  * `.Nb::Int`: grid index first trailing point
  * `.N::Int`: grid index last point
  * `.nodes::Int`: number of nodes in reduced wavefunction (r ≠ 0)
  * `.ΔNlctp::Float64`: lctp offset with respect to Nlctp (1.0 ≤ ΔN ≤ 1.0)
  * `.ΔNuctp::Float64`: uctp offset with respect to Nuctp (-1.0 ≤ ΔN ≤ 0.0)

Mutable struct to hold special grid indices as well as the number of nodes and the (negative) offset of the exact uctp with respect to Nuctp. `Pos` is one of the fields of the [`Def`](@ref) object

#### Examples:

```
julia> pos = Pos(1, 2, 3, 4, 5, 6, 7, 8.0, 9.0, 10.0);
julia> pos.Nuctp
4

julia> pos.Nuctp = 8;
julia> pos
Pos(1, 2, 3, 8, 5, 6, 7, 8.0, 9.0, 10.0)
```
