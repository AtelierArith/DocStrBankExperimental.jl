```
amplifier([Td=Vector{Float64}, Tt=Matrix{Float64},] basis::SymplecticBasis, r<:Real, n<:Int)
```

入力単一モードガウス状態とその環境との相互作用を二モード圧縮操作を介して記述するガウスチャネル。チャネルは圧縮振幅パラメータ `r` と熱雑音 `n` によってパラメータ化されます。

## アンプチャネルの数学的説明

アンプチャネル `A(r, nₜₕ)` は、`r` が圧縮振幅パラメータであり、`nₜₕ ≥ 1` が熱雑音パラメータであるとき、ゼロ変位ベクトル、変換行列 `cosh(r)I`、および雑音行列 `nₜₕsinh²(r)I` によって特徴付けられます。

## 例

```jldoctest
julia> amplifier(QuadPairBasis(1), 2.0, 3)
GaussianChannel for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
transform: 2×2 Matrix{Float64}:
 3.7622  0.0
 0.0     3.7622
noise: 2×2 Matrix{Float64}:
 39.4623   0.0
  0.0     39.4623
```
