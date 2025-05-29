```
StructArray{T}(undef, dims; unwrap=T->false)
```

要素型 `T` の初期化されていない `StructArray` を、`Array` フィールド配列を持つ形で構築します。

`unwrap` キーワード引数は、要素型 `T` の配列を再帰的に `StructArray` に変換するかどうかを決定する関数です。

# 例

```julia-repl
julia> StructArray{ComplexF64}(undef, (2,3))
2×3 StructArray(::Array{Float64,2}, ::Array{Float64,2}) with eltype Complex{Float64}:
  2.3166e-314+2.38405e-314im  2.39849e-314+2.38405e-314im  2.41529e-314+2.38405e-314im
 2.31596e-314+2.41529e-314im  2.31596e-314+2.41529e-314im  2.31596e-314+NaN*im
```
