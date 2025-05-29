```
collect_group_members(
    group_indices::AbstractVector{T},
)::Vector{Vector{T}} where {T <: Integer}
```

Given an array `group_indices` which assigns each entry of some axis to a non-negative group index (with zero meaning "no group"), where the group indices are compact (in the range `1...N`), return a vector of vectors, one for each group, containing the (sorted) indices of the entries of the group.
