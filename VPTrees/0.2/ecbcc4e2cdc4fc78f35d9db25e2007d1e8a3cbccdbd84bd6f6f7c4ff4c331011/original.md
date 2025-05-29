```
VPTree(data::Vector{InputType}, metric; threaded=nothing)
```

Construct Vantage Point Tree with a vector of `data` and given a callable `metric`. `threaded` uses threading is only avaible in Julia 1.3+ to parallelize construction of the Tree. When not explicitly set, is set to true when the necessary conditions are met.

## Example:

```julia
using VPTrees
using StringDistances

data = ["bla", "blub", "asdf", ":assd", "ast", "baube"]
vptree = VPTree(data, Levenshtein())
query = "blau"
radius = 2
data[find(vptree, query, radius)]
# 2-element Array{String,1}:
#  "bla"
#  "blub"
n_neighbors = 3
data[find_nearest(vptree, query, n_neighbors)]
# 3-element Array{String,1}:
#  "baube"
#  "blub"
#  "bla"
```
