```
double_binary_tree(k::Integer)
```

Create a double complete binary tree with `k` levels.

### References

  * Used as an example for spectral clustering by Guattery and Miller 1998.

# Examples

```jldoctest
julia> using Graphs

julia> double_binary_tree(4)
{30, 29} undirected simple Int64 graph

julia> double_binary_tree(Int8(5))
{62, 61} undirected simple Int8 graph
```
