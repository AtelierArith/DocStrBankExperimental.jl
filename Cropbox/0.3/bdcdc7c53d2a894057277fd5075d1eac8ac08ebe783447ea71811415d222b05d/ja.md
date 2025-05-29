```
plot!(p, <arguments>; <keyword arguments>) -> Plot
```

既存の `Plot` オブジェクト `p` を更新し、`plot` で作成した新しいグラフを追加します。

関連情報: [`plot`](@ref)

# 引数

  * `p::Union{Plot,Nothing}`: 更新されるプロットオブジェクト; `nothing` は新しいプロットを作成します。
