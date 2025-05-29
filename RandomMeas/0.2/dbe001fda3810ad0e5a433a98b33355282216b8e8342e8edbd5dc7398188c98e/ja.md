```
partial_trace(shadows::AbstractArray{<:AbstractShadow}, subsystem::Vector{Int})
```

コレクション内の各シャドウの部分トレースを計算します。

# 引数

  * `shadows::AbstractArray{<:AbstractShadow}`: シャドウオブジェクトのコレクション（ベクトルまたは2D配列）。
  * `subsystem::Vector{Int}`: 保持するサブシステムを指定するサイトインデックスのベクトル（1ベース）。

# 戻り値

指定されたサブシステムに減少したシャドウの配列で、入力配列と同じ次元を持ちます。
