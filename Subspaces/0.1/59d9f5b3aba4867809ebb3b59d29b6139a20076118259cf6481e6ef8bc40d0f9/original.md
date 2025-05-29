```
Subspace(basis::AbstractArray{AbstractArray{N}, 1}; tol::Real=1.0e-6)
```

Create a subspace from the given basis, expressed as a list of basis vectors.

```
Subspace(basis::AbstractArray{N+1}; tol::Real=1.0e-6)
```

Create a subspace from a basis given as a multi-dimensional array.  The last array index enumerates the basis elements.  E.g., if given a matrix this constructor will create a subspace representing the column span of that matrix.

The `tol` parameter sets the tolerance for determining whether vectors are linearly dependent.

  * `basis::Array`: An orthonormal basis for this subspace.  The final index of this array indexes the basis vectors.
  * `perp::Array`: An orthonormal basis for the perpendicular subspace.
  * `tol::AbstractFloat`: The tolerance for determining whether vectors are linearly dependent.

```jldoctest
julia> Subspace([[1, 2, 3], [4, 5, 6]]) == Subspace([ 1 4; 2 5; 3 6])
true
```
