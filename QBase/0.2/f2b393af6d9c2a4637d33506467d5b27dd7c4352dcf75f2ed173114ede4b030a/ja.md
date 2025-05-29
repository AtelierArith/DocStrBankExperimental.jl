```
Ket(ψ :: Vector{T}; atol=ATOL :: Float64) where T <: Number
```

複素値ヒルベルト空間上の正規化された列ベクトルです。随伴ベクトル `ψ'` で呼び出された場合、構築時に随伴が取られます。

```julia
Ket(ψ :: Adjoint{Vector{T}}; atol=ATOL :: Float64) where T <: Number
```

同様に、`Bra` は随伴を介して `Ket` に変換できます。

```julia
Ket(ψ :: Bra{T}; atol=ATOL :: Float64) where T <: Number
```

`Ket(ψ)` は、`ψ` が正規化されていない場合に `DomainError` をスローします。
