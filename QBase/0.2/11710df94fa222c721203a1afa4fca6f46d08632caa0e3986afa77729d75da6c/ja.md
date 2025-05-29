```
is_braket( ψ :: Vector; atol=ATOL :: Float64) :: Bool

is_braket(
    ψ :: Adjoint{T, Vector{T}};
    atol=ATOL :: Float64
) where T <: Number :: Bool
```

ベクトル `ψ` が有効なブラ（またはケット）である場合、`true` を返します：

  * `ψ` は実数または複素数の値を持つベクトルです。
  * `ψ` はブラケット内積に関して正規化されています（`ψ' * ψ == 1`）。
