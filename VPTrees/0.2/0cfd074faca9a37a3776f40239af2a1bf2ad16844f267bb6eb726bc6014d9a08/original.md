```
find(vptree::VPTree{InputType, MetricReturnType}, query::InputType, radius::MetricReturnType, skip=nothing)::Vector{Int}
```

Find all items in `vptree` within `radius` of `query` with respect to the metric defined in the VPTree. Returns indices into VPTree.data. The optional `skip` argument is a function `f(::Int)::Bool` which can be used to omit points in the tree from the search based on their index.

## Example

```julia
using VPTrees
using StringDistances

data = ["bla", "blub", "asdf", ":assd", "ast", "baube"]
metric = (a, b) -> evaluate(Levenshtein(),a,b)
vptree = VPTree(data, metric)
query = "blau"
radius = 2
data[find(vptree, query, radius)]
# 2-element Array{String,1}:
#  "bla"
#  "blub"
```
