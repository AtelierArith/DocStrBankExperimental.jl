```
group_names(
    daf::DafReader,
    axis::AbstractString,
    entries_of_groups::AbstractVector{<:AbstractVector{<:Integer}};
    prefix::AbstractString,
)::Vector{String}
```

Given an `entries_of_groups` vector of vectors, one for each group, containing the (sorted) indices of the entries of the group along some `axis` of some `daf` data set, return a vector giving a unique name for each group. This name consists of the `prefix`, followed by the index of the group, followed by a `.XX` two-digit suffix which is a hash of the names of the axis entries of the group.

The returned names strike a balance between readability and safety. A name like `M123.89` for group #123 is easy to deal with manually, but is also reasonably safe in the common use case that groups are re-computed, and there is per-group metadata lying around associated with the old groups, as the probability of the new group #123 having the same suffix is only 1% (unless it is actually identical).
