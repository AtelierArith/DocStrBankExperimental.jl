```
r2star_numart2s!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> r2s
```

リアルタイムT2*マッピングの数値アルゴリズム (NumART2*) [1].

### 引数

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2*マップ (1 / TEsの単位)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味領域のバイナリマスク

### 戻り値

  * `r2s`: R2*マップ (1 / TEsの単位)

### 参考文献

[1] Hagberg GE, Indovina I, Sanes JN, Posse S. リアルタイムでのT2*変化の定量化のためのマルチエコー平面イメージングと数値的方法を使用した。医学における磁気共鳴: 国際磁気共鳴医学会の公式ジャーナル。2002年11月;48(5):877-82.
