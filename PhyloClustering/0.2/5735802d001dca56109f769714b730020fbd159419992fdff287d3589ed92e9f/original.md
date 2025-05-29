```
show_bipartitions(n::Int64; start::Int64 = 0, stop::Int64=-1)
```

Show the bipartitions between certain indices for a given number of taxa.

# Arguments

  * `n`: the number of taxa
  * `start`(defaults to `0`): the starting index.
  * `stop`(defaults to `-1`): the ending index.

# Output

The bipartiions of trees with `n` taxa between `start` index and `stop` index.

# Example

```jldoctest
julia> show_bipartitions(4,stop = 4)
idx	partition
0	1 | 2 3 4 
1	2 | 1 3 4 
2	3 | 1 2 4 
3	4 | 1 2 3 
4	1 2 | 3 4 
```
