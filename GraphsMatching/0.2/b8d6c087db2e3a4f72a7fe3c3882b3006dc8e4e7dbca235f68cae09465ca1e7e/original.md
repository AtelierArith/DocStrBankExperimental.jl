```
struct MatchingResult{U}
    weight::U
    mate::Vector{Int}
end
```

A type representing the result of a matching algorithm.

```
weight: total weight of the matching

mate:    `mate[i] = j` if vertex `i` is matched to vertex `j`.
         `mate[i] = -1` for unmatched vertices.
```
