```
partial_transpose(shadows::AbstractArray{<:AbstractShadow}, subsystem::Vector{Int})
```

コレクション内の各シャドウに対して部分転置を計算します。

# 引数

  * `shadows::AbstractArray{<:AbstractShadow}`: シャドウオブジェクトのコレクション（ベクターまたは2D配列）。
  * `subsystem::Vector{Int}`: 転置を行うサブシステムを指定するサイトインデックスのベクター（1ベース）。

# 戻り値

入力の次元を保持しながら部分転置が適用されたシャドウオブジェクトの配列。
