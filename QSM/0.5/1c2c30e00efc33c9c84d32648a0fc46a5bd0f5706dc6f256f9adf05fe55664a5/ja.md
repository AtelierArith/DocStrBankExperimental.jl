```
tkd(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :k,
    thr::Real = 0.15,
) -> typeof(similar(f))
```

切断されたk空間分割（TKD）[1].

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された（マルチエコー）局所場/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `pad::NTuple{3, Integer} = (0, 0, 0)`: ゼロパディング配列

      * `< 0`: パディングなし
      * `≥ 0`: 高速fftサイズへの最小パディング
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: Bフィールド方向の単位ベクトル
  * `Dkernel::Symbol = :k`: 双極子カーネル法
  * `thr::Real = 0.15`: k空間フィルターの閾値

### 戻り値

  * `typeof(similar(f))`: 感受性マップ

### 参考文献

[1] Shmueli K, de Zwart JA, van Gelderen P, Li TQ, Dodd SJ, Duyn JH. 磁気共鳴画像（MRI）位相データを用いた生体脳組織の磁気感受性マッピング. 磁気共鳴医学: 国際磁気共鳴医学会の公式ジャーナル. 2009年12月;62(6):1510-22.
