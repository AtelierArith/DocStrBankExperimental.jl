```
r2star_ll!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> r2s
```

対数線形フィット。

### 引数

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2* マップ (1 / TEs の単位)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味のある領域のバイナリマスク

### 戻り値

  * `r2s`: R2* マップ (1 / TEs の単位)
