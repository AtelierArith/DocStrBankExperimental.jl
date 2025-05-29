```
compact_groups!(
    group_indices::AbstractVector{<:Integer},
)::Int
```

Given an array `group_indices` which assigns each entry of some axis to a non-negative group index (with zero meaning "no group"), compact it in-place so that the group indices will be `1...N`, and return `N`.
