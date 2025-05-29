```
r2star_numart2s(
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> typeof(similar(mag, size(mag)[1:N-1]))
```

リアルタイムT2*マッピングの数値アルゴリズム (NumART2*) [1].

### 引数

  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味領域のバイナリマスク

### 戻り値

  * `typeof(similar(mag, size(mag)[1:N-1]))`: R2*マップ (1 / TEsの単位)

### 参考文献

[1] Hagberg GE, Indovina I, Sanes JN, Posse S. マルチエコー平面イメージングと数値的方法を用いたT2*変化のリアルタイム定量化. 磁気共鳴医学: 国際磁気共鳴医学会の公式ジャーナル. 2002年11月;48(5):877-82.
