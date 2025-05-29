```
tsvd(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :k,
    thr::Real = 0.15,
) -> typeof(similar(f))
```

切断特異値分解 (TSVD) [1].

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された (マルチエコー) ローカルフィールド/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `pad::NTuple{3, Integer} = (0, 0, 0)`: ゼロパディング配列

      * `< 0`: パディングなし
      * `≥ 0`: 高速FFTサイズへの最小パディング
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: Bフィールド方向の単位ベクトル
  * `Dkernel::Symbol = :k`: ダイポールカーネル法
  * `thr::Real = 0.15`: k空間フィルターの閾値

### 戻り値

  * `typeof(similar(f))`: 感受性マップ

### 参考文献

[1] Wharton S, Schäfer A, Bowtell R. 人間の脳における感受性マッピング：閾値ベースのk空間分割を使用。医学における磁気共鳴。2010年5月;63(5):1292-304.
