```
standard_violation(t::Tabloid)
```

Return the index of the first violation to the standardness of the tabloid `t`, i.e. the first index where `t[i,j]` > `t[i+1, j]` with regard to the ordering. Otherwise return `nothing`.

# Examples:

```jldoctest
julia> standard_violation(Tabloid([1 2 3; 1 4 5; 1 5 6; 2 3 4], [1,2,3,4,5,6]))
CartesianIndex(3, 2)
```

```jldoctest
julia> standard_violation(Tabloid([1 2 3; 1 2 4], [1,2,3,4]))

```
