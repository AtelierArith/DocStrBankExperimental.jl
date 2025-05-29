```
array_of_ranges = kfoldperm(N, k; breaks=[])
```

Divides a list of indices from 1 to `N` into `k` groups.

# Arguments

  * `N`: (`::Integer`) number of elements to be ordered
  * `k`: (`::Integer`) number of groups to divide the `N` elements.

# Keywords

  * `breaks`: (`::Vector{<:Integer}`, `=[]`) array of indices where predefined breakpoints are   placed.

# Returns

  * `array_of_ranges`: (`::Vector{UnitRange{<:Integer}}`) array containing ranges of different   groups. The target is `k` groups, but this could increase by adding elements to the   `breaks` input array
