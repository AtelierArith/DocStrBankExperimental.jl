```
ChoiOp( Λ :: AbstractMatrix, dims :: Vector{Int} ) :: ChoiOp{<:Number}
ChoiOp( 𝒩 :: Function, dims :: Vector{Int} ) :: ChoiOp{ComplexF64}
```

量子チャネルのChoi演算子表現を構築します。入力として関数 `𝒩` または一連のクローズ演算子が提供されると、Choi行列は[`choi_matrix`](@ref)メソッドを使用して構築されます。

`ChoiOp`型には以下のフィールドが含まれています：

  * `M :: Matrix{<:Number}` - Choi行列。
  * `dims :: Vector{Int}` - チャネルの入力/出力次元 `[dim_in, dim_out]`。

[`is_choi_matrix`](@ref)が`false`を返す場合、`DomainError`がスローされます。
