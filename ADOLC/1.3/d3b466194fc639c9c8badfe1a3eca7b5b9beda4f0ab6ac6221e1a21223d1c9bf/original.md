```
create_partial_cxx_identity(n::I_1, idxs::Vector{I_2}) where {I_1 <: Integer, I_2 <: Integer}
```

Creates a matrix of shape (`n`, `length(idxs)`) of type CxxPtr{CxxPtr{Float64}} (wrapper of C++'s double**). The columns are canonical basis vectors corresponding to the entries of `idxs`. The order of the basis vectors is defined by the order of the indices in `idxs`. Details about the application can be found in this [guide](@ref "Seed-Matrix").

!!! warning
    The number of rows `n` must be smaller than the maximal index of `idxs`!


!!! warning
    The values of `idxs` must be non-negative!


# Examples

```jldoctest
n = 4
idxs = [1, 3]
id = CxxMatrix(create_partial_cxx_identity(n, idxs), n, length(idxs))
# output

4×2 CxxMatrix:
 1.0  0.0
 0.0  0.0
 0.0  1.0
 0.0  0.0
```

The order in `idxs` defines the order of the basis vectors.

```jldoctest
n = 3
idxs = [3, 0, 1]
id = CxxMatrix(create_partial_cxx_identity(n, idxs), n, length(idxs))


# output

3×3 CxxMatrix:
 0.0  0.0  1.0
 0.0  0.0  0.0
 1.0  0.0  0.0
```
