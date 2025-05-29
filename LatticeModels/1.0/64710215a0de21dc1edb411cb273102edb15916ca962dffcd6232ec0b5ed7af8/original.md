```
LatticeValue(lat, values)
```

Constructs a LatticeValue object.

## Arguments

  * `lat`: the lattice the value is defined on.
  * `values`: an `AbstractVector` of values on the lattice.

## Example

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(2, 2);

julia> LatticeValue(l, [1, 2, 3, 4])    # Custom values
LatticeValue{Int64} on a 4-site SquareLattice in 2D space
Values stored in a Vector{Int64}:
[1, 2, 3, 4]

julia> x = LatticeValue(l, :x)          # x-coordinate
LatticeValue{Float64} on a 4-site SquareLattice in 2D space
Values stored in a Vector{Float64}:
[1.0, 1.0, 2.0, 2.0]

julia> l2 = SquareLattice(3, 3);

julia> y = LatticeValue(l2, :y)          # y-coordinate
LatticeValue{Float64} on a 9-site SquareLattice in 2D space
Values stored in a Vector{Float64}:
[1.0, 2.0, 3.0, 1.0, 2.0, 3.0, 1.0, 2.0, 3.0]

julia> x + y
ERROR: Matching lattices expected.
Got following:
  #1: 4-site SquareLattice in 2D space
  #2: 9-site SquareLattice in 2D space
[...]
```
