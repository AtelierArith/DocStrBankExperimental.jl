```
cmp_stat(stat_dist, v)
```

Calculate proportion of elements below or above a given statistic value.

# Arguments

  * `stat_dist::AbstractVector`: statistic values distribution
  * `v::Real`: statistic value
  * `type::Symbol=:g`: calculation proportion of elements greater (`:g`) or lesser (`:l`) than `v`

# Returns

  * `p::Float64`
