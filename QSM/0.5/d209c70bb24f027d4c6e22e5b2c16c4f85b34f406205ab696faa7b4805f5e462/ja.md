```
rts(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    Dkernel::Symbol = :k,
    bdir::NTuple{3, Real} = (0, 0, 1),
    lstol::Integer = 4,
    delta::Real = 0.15,
    mu::Real = 1e5,
    rho::Real = 10,
    tol::Real = 1e-2,
    maxit::Integer = 20,
    verbose::Bool = false,
) -> typeof(similar(f))
```

スパース事前条件を用いた迅速な二段階ダイポール反転 [1].

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
  * `lstol::Integer = 4`: lsmrソルバーの停止許容誤差（反復回数）
  * `delta::Real = 0.15`: 条件の悪いk空間領域の閾値
  * `mu::Real = 1e5`: tv最小化のための正則化パラメータ
  * `rho::Real = 10`: ラグランジュ乗数ペナルティパラメータ
  * `tol::Real = 1e-2`: 停止許容誤差
  * `maxit::Integer = 20`: 最大反復回数
  * `verbose::Bool = false`: 収束情報を表示

### 戻り値

  * `typeof(similar(f))`: 感受率マップ

### 参考文献

[1] Kames C, Wiggermann V, Rauscher A. スパース事前条件を用いた感受率マッピングのための迅速な二段階ダイポール反転. Neuroimage. 2018年2月15日;167:276-83.
