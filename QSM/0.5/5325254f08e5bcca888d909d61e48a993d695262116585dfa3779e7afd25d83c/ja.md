```
sharp(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    r::Real = 18*minimum(vsz),
    thr::Real = 0.05,
) -> Tuple{typeof(similar(f)), typeof(similar(mask))}
```

位相データのための高度な調和アーティファクト除去（SHARP）[1]。

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: アンラップされた（マルチエコー）フィールド/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: smvカーネルのボクセルサイズ

### キーワード

  * `r::Real = 18*minimum(vsz)`: `vsz`の単位でのsmvカーネルの半径
  * `thr::Real = 0.05`: ハイパスフィルターの閾値

### 戻り値

  * `typeof(similar(f))`: 背景補正されたローカルフィールド/位相
  * `typeof(similar(mask))`: 膨張されたバイナリマスク

### 参考文献

[1] Schweser F, Deistung A, Lehr BW, Reichenbach JR. 定量的なMRI信号位相を用いた内因性磁気組織特性のイメージング：in vivo脳鉄代謝へのアプローチ？. Neuroimage. 2011年2月14日;54(4):2789-807.
