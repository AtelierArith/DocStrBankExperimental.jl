```
Assembly{TF, TP<:AbstractVector{<:AbstractVector{TF}},
    TC<:AbstractVector{<:Integer}, TE<:AbstractVector{Element{TF}}}
```

接続された非線形ビーム要素のアセンブリを定義する複合型です。

# フィールド

  * `points`: すべてのビーム要素のエンドポイントの配列
  * `start`: 各ビーム要素が開始するポイントインデックスを含む配列
  * `stop`: 各ビーム要素が停止するポイントインデックスを含む配列
  * `elements`: ビーム要素の定義を含む配列（[`Element`](@ref)を参照）
