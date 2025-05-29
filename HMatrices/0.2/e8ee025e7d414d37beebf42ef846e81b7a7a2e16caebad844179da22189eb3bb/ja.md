```
struct CardinalitySplitter <: AbstractSplitter
```

`ClusterTree`を`length(tree)>nmax`の場合に最も大きな次元に沿って分割するために使用されます。分割は、`data`がすべての子に均等に分配されるように行われます。

## 参照: [`AbstractSplitter`](@ref)
