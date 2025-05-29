```
attenuator([Td=Vector{Float64}, Tt=Matrix{Float64},] basis::SymplecticBasis, theta<:Real, n<:Int)
```

入力単一モードガウス状態とその環境との結合をビームスプリッタ操作を介して記述するガウスチャネル。このチャネルは、ビームスプリッタの回転角 `theta` と熱雑音 `n` によってパラメータ化されます。

## 減衰器チャネルの数学的説明

減衰器チャネル `E(θ, nₜₕ)` は、`θ` がビームスプリッタの回転パラメータであり、`nₜₕ ≥ 1` が熱雑音パラメータであるとき、ゼロ変位ベクトル、変換行列 `cos(θ)I`、およびノイズ行列 `nₜₕsin²(θ)I` によって特徴付けられます。

## 例

```jldoctest
julia> attenuator(QuadPairBasis(1), pi/6, 3)
GaussianChannel for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
transform: 2×2 Matrix{Float64}:
 0.866025  0.0
 0.0       0.866025
noise: 2×2 Matrix{Float64}:
 0.75  0.0
 0.0   0.75
```
