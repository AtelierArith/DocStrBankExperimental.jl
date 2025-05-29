```
get_majority_set(counts, uranks::Vector{Vector{T}}) where {T}
```

Returns the smallest set of candidates who are strictly preferred to candidates not in the set. 

# Arguments

  * `uranks`: a vector of unique rankings. Each ranking is a vector in which index represents rank and value represents candidate id.
  * `counts`: a vector of frequency counts corresponding to each unique ranking
