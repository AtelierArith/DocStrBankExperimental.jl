```
new_address, value = hopnextneighbour(add, chosen, boundary_condition)
```

Compute the new address of a hopping event for the Hubbard model. Returns the new address and the square root of product of occupation numbers of the involved modes multiplied by a term consistent with boundary condition as the `value`.  The following boundary conditions are supported:

  * `:periodic`: hopping over the boundary gives does not change the `value`.
  * `:twisted`: hopping over the boundary flips the sign of the `value`.
  * `:hard_wall`: hopping over the boundary gives a `value` of zero.
  * `θ <: Number`: hopping over the boundary gives a `value` multiplied by $\exp(iθ)$ or $\exp(−iθ)$ depending on the direction of hopping.

The off-diagonals are indexed as follows:

  * `(chosen + 1) ÷ 2` selects the hopping site.
  * Even `chosen` indicates a hop to the left.
  * Odd `chosen` indicates a hop to the right.

# Example

```jldoctest
julia> using Rimu.Hamiltonians: hopnextneighbour

julia> hopnextneighbour(BoseFS(1, 0, 1), 3)
(BoseFS{2,3}(2, 0, 0), 1.4142135623730951)

julia> hopnextneighbour(BoseFS(1, 0, 1), 4)
(BoseFS{2,3}(1, 1, 0), 1.0)

julia> hopnextneighbour(BoseFS(1, 0, 1), 3, :twisted)
(BoseFS{2,3}(2, 0, 0), -1.4142135623730951)

julia> hopnextneighbour(BoseFS(1, 0, 1), 3, :hard_wall)
(BoseFS{2,3}(2, 0, 0), 0.0)

julia> hopnextneighbour(BoseFS(1, 0, 1), 3, π/4)
(BoseFS{2,3}(2, 0, 0), 1.0000000000000002 + 1.0im)
```
