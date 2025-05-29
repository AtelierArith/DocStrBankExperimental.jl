```
r2star_arlo!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing
) -> r2s
```

線形操作における自己回帰 (ARLO) [1].

### 引数

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2* マップ (1 / TEs の単位)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: マルチエコーの大きさ
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味のある領域のバイナリマスク

### 戻り値

  * `r2s`: R2* マップ (1 / TEs の単位)

### 参考文献

[1] Pei M, Nguyen TD, Thimmappa ND, Salustri C, Dong F, Cooper MA, Li J,     Prince MR, Wang Y. 自己回帰に基づく高速単指数フィッティングのためのアルゴリズム     線形操作 (ARLO) のデータ.     磁気共鳴医学. 2015年2月;73(2):843-50.
