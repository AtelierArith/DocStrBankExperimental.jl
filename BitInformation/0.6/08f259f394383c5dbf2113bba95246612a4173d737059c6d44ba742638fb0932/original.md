```
H = bitcount_entropy(A::AbstractArray{T},base::Real=2) where {T<:Union{Integer,AbstractFloat}}
```

Returns a vector `H` of entropies for the occurence of 0,1 in every bit position in `T` across elements of `A`. Makes use of the `bitcount` functions and calculates the entropy from the probability of the 0 and 1 bit. The base `base` is by default 2, such that the unit of entropy is bit.
