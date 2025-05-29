```
load(filename::AbstractString)
```

名前 `filename` の BVH ファイルを読み込み、`BVHGraph` を返します。

# 例

```julia
julia> g = load("Test.bvh")
BVHGraph
Name: Test.bvh
[...]
```
