```
R = redundancy(A::AbstractArray{T},B::AbstractArray{T}) where {T<:Union{Integer,AbstractFloat}}
```

Bitwise redundancy of two arrays A,B. Redundancy is a normalised measure of the mutual information: 1 for always identical/opposite bits, 0 for no mutual information.
