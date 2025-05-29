```
enclose(A::AbstractMatrix{T}, b::AbstractVector{T}) where {T<:Interval}
```

Computes an enclosure of the solution of the interval linear system $Ax=b$ using the algorithm described in sec. 5.7.1 of [[HOR19]](@ref).
