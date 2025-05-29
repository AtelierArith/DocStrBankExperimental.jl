```
r2star_ll(
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> typeof(similar(mag, size(mag)[1:N-1]))
```

対数線形フィット。

### 引数

  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコー振幅
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味領域のバイナリマスク

### 戻り値

  * `typeof(similar(mag, size(mag)[1:N-1]))`: R2* マップ (TEsの単位あたり1)
