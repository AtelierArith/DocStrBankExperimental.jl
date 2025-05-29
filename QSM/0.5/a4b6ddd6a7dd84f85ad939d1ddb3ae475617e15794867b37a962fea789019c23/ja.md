```
tikh(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :k,
    lambda::Real = 1e-2,
    reg::Symbol = :gradient
) -> typeof(similar(f))
```

ティホノフ正則化 [1].

$$
    argmin_x ||Dx - f||_2^2 + \frac{λ}{2}||Γx||_2^2
$$

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された（マルチエコー）局所場/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `pad::NTuple{3, Integer} = (0, 0, 0)`: ゼロパディング配列

      * `< 0`: パディングなし
      * `≥ 0`: 高速fftサイズへの最小パディング
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: Bフィールド方向の単位ベクトル
  * `Dkernel::Symbol = :k`: ダイポールカーネル法
  * `lambda::Real = 1e-2`: 正則化パラメータ
  * `reg::Symbol = :identity`: 正則化行列 Γ   (`:identity`, `:gradient`, `:laplacian`)

### 戻り値

  * `typeof(similar(f))`: 感受率マップ

### 参考文献

[1] Bilgic B, Chatnuntawech I, Fan AP, Setsompop K, Cauley SF, Wald LL,     Adalsteinsson E. Fast image reconstruction with L2‐regularization. Journal     of magnetic resonance imaging. 2014 Jul;40(1):181-91.
