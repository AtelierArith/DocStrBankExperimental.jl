```
find_nearest(vptree::VPTree{InputType, MetricReturnType}, query::InputType, n_neighbors::Int, skip=nothing)::Vector{Int}
```

Find `n_neighbors` items in `vptree` closest to `query` with respect to the metric defined in the VPTree. Returns indices into VPTree.data. The optional `skip` argument is a function `f(::Int)::Bool` which can be used to omit points in the tree from the search based on their index.

## Example:

```julia
using VPTrees
using StringDistances

data = ["bla", "blub", "asdf", ":assd", "ast", "baube"]
metric = (a, b) -> evaluate(Levenshtein(),a,b)
vptree = VPTree(data, metric)
query = "blau"
n_neighbors = 3
data[find_nearest(vptree, query, n_neighbors)]
# 3-element Array{String,1}:
#  "baube"
#  "blub"
#  "bla"
```
