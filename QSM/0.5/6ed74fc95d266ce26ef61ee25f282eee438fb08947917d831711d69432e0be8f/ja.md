```
nltv(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing,
    Wtv::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing,
    pad::NTuple{3, Integer} = (0, 0, 0),
    Dkernel::Symbol = :k,
    bdir::NTuple{3, Real} = (0, 0, 1),
    lambda::Real = 1e-3,
    rho::Real = 100*lambda,
    mu::Real = 1,
    tol::Real = 1e-3,
    maxit::Integer = 250,
    toln::Real = 1e-6,
    maxitn::Integer = 10,
    verbose::Bool = false,
) -> typeof(similar(f))
```

ADMMを使用した非線形全変動デコンボリューション [1].

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された（マルチエコー）局所場/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing`: データ忠実度重み
  * `Wtv::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, 5)}} = nothing`: 全変動重み

      * `M = 3`: すべての3つの勾配方向とすべてのエコーに対して同じ重み
      * `M = 4 = N`: すべての3つの勾配方向に対して同じ重み、エコーに対して異なる重み
      * `M = 5, (size(Wtv)[4,5] = [1 or N, 3]`: 各勾配方向に対して異なる重み
  * `pad::NTuple{3, Integer} = (0, 0, 0)`: ゼロパディング配列

      * `< 0`: パディングなし
      * `≥ 0`: 高速fftサイズへの最小パディング
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: Bフィールド方向の単位ベクトル
  * `Dkernel::Symbol = :k`: ダイポールカーネル法
  * `lambda::Real = 1e-3`: 正則化パラメータ
  * `rho::Real = 100*lambda`: ラグランジュ乗数ペナルティパラメータ
  * `mu::Real = 1`: ラグランジュ乗数ペナルティパラメータ（`W = nothing`の場合は未使用）
  * `tol::Real = 1e-3`: 停止許容誤差
  * `maxit::Integer = 250`: 最大反復回数
  * `toln::Real = 1e-6`: ニュートン法の停止許容誤差
  * `maxitn::Integer = 10`: ニュートン法の最大反復回数
  * `verbose::Bool = false`: 収束情報を印刷

### 戻り値

  * `typeof(similar(f))`: 感受率マップ

### 参考文献

[1] Milovic C, Bilgic B, Zhao B, Acosta‐Cabronero J, Tejos C. Fast nonlinear     susceptibility inversion with variational regularization.     Magnetic resonance in medicine. 2018 Aug;80(2):814-21.
