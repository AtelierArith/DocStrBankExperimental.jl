```
VPTree(data::Vector{InputType}, metric; threaded=nothing)
```

ベンテージポイントツリーを`data`のベクターと指定された呼び出し可能な`metric`で構築します。`threaded`は、ツリーの構築を並列化するためにJulia 1.3+でのみ利用可能なスレッドを使用します。明示的に設定されていない場合、必要な条件が満たされているときにtrueに設定されます。

## 例:

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
