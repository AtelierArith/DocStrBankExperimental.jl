```
extendtraces!(::Plot, ::Dict{Union{Symbol,AbstractString},AbstractVector{Vector{Any}}}), indices, maxpoints)
```

1つ以上のトレースにデータを追加します。更新辞書の構造について覚えておくべきいくつかの注意点があります：

  * 辞書のキーは、更新するトレース属性を指定する `Symbol` または `AbstractString` 型である必要があります。これらの属性はトレースに既に存在している必要があります。
  * 辞書の値は、データの `Vector` の `Vector` でなければなりません。外側のインデックスはPlotlyにどのトレースを更新するかを示し、そのインデックスの `Vector` にはトレース属性に追加される値が含まれています。

これらの概念は例を通じて最もよく理解されます：

```julia
# 最初のトレースのy属性の末尾に値[1, 3]を追加し、
# ポイントを削除しません
extendtraces!(p, Dict(:y=>Vector[[1, 3]]), [1], -1)
extendtraces!(p, Dict(:y=>Vector[[1, 3]]))  # 上記と同等
```

```julia
# 第三のトレースのmarker.size属性の末尾に値[1, 3]を追加し、
# 第5のトレースのmarker.sizeの末尾に[5,5,6]を追加します -- 各marker.size属性につき最大10ポイントを残します
extendtraces!(p, Dict("marker.size"=>Vector[[1, 3], [5, 5, 6]]), [3, 5], 10)
```
