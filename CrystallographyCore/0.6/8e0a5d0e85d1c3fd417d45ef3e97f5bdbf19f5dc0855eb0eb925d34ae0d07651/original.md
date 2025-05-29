```
Lattice(data::AbstractMatrix)
```

Construct a `Lattice` from a matrix.

!!! note
    The basis vectors of the matrix are stored as columns.


# Examples

```jldoctest
julia> Lattice([
           1.2 4.5 7.8
           2.3 5.6 8.9
           3.4 6.7 9.1
       ])
Lattice{Float64}
 1.2  4.5  7.8
 2.3  5.6  8.9
 3.4  6.7  9.1
```
