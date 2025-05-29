```
strictly_upper_triangular_matrix(L::AbstractVector{T}) where {T <: NCRingElement}
```

Return the $n$ by $n$ matrix whose entries above the main diagonal are the elements of `L`, and which has zeroes elsewhere. The value of $n$ is determined by the condition that `L` has length $(n-1)n/2$.

An exception is thrown if there is no integer $n$ with this property.

# Examples

```jldoctest
julia> strictly_upper_triangular_matrix([1, 2, 3])
[0   1   2]
[0   0   3]
[0   0   0]
```
