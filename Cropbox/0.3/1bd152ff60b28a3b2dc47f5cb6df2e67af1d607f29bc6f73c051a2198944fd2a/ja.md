```
visualize!(p, <arguments>; <keyword arguments>) -> Plot
```

既存の `Plot` オブジェクト `p` を更新し、`visualize` で作成された新しいグラフを追加します。

参照: [`visualize`](@ref)

# 引数

  * `p::Union{Plot,Nothing}`: 更新されるプロットオブジェクト; `nothing` は新しいプロットを作成します。
