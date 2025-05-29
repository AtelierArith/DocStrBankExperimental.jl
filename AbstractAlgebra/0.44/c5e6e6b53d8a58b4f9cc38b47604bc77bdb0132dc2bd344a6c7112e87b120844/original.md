```
lower_triangular_matrix(L::AbstractVector{T}) where {T <: NCRingElement}
```

Return the $n$ by $n$ matrix whose entries on and below the main diagonal are the elements of `L`, and which has zeroes elsewhere. The value of $n$ is determined by the condition that `L` has length $n(n+1)/2$.

An exception is thrown if there is no integer $n$ with this property.

# Examples

```jldoctest
julia> lower_triangular_matrix([1, 2, 3])
[1   0]
[2   3]
```
