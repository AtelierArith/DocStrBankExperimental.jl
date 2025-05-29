```
find(vptree::VPTree{InputType, MetricReturnType}, query::InputType, radius::MetricReturnType, skip=nothing)::Vector{Int}
```

`vptree`内の`query`から`radius`以内のすべてのアイテムを、VPTreeで定義されたメトリックに基づいて見つけます。VPTree.dataへのインデックスを返します。オプションの`skip`引数は、インデックスに基づいてツリー内のポイントを検索から省略するために使用できる関数`f(::Int)::Bool`です。

## 例

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
