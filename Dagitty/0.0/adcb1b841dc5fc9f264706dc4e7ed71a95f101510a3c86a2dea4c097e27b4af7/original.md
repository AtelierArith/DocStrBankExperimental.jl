```
DAGHasLoops
```

Exception, thrown when loops are detected on DAG construction.

# Examples

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :B, :B => :A)
ERROR: DAGHasLoops()
```
