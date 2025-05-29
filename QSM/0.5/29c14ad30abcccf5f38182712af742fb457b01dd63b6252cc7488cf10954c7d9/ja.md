```
r2star_arlo(
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> typeof(similar(mag, size(mag)[1:N-1]))
```

線形操作における自己回帰 (ARLO) [1].

### 引数

  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味のある領域のバイナリマスク

### 戻り値

  * `typeof(similar(mag, size(mag)[1:N-1]))`: R2* マップ (TEsの単位で1 / )

### 参考文献

[1] Pei M, Nguyen TD, Thimmappa ND, Salustri C, Dong F, Cooper MA, Li J,     Prince MR, Wang Y. 自己回帰に基づくデータの線形操作に関する高速単指数フィッティングのためのアルゴリズム (ARLO).     磁気共鳴医学. 2015年2月;73(2):843-50.
