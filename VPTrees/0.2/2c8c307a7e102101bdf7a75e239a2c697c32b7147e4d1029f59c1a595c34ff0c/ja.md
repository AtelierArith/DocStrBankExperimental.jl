```
find_nearest(vptree::VPTree{InputType, MetricReturnType}, query::InputType, n_neighbors::Int, skip=nothing)::Vector{Int}
```

`vptree`内の`query`に最も近い`n_neighbors`個のアイテムを、VPTreeで定義されたメトリックに基づいて見つけます。VPTree.dataへのインデックスを返します。オプションの`skip`引数は、インデックスに基づいてツリー内のポイントを検索から省略するために使用できる関数`f(::Int)::Bool`です。

## 例:

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
