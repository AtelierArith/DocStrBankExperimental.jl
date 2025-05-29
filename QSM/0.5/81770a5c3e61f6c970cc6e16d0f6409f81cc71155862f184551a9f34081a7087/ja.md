```
multi_echo_linear_fit(
    phas::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real};
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing,
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
    phase_offset::Bool = true
) -> Tuple{typeof(similar(phas)){N-1}, [typeof(similar(phas)){N-1}]}
```

(重み付き) 最小二乗法によるマルチエコーデータのフィッティング。

### 引数

  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: アンワップされたマルチエコーフェーズ
  * `TEs::AbstractVector{<:Real}`: エコー時間

### キーワード

  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing`:   重みの平方根、例えばボクセルの誤差分散の逆数   ~> W² = 1/σ²(phas) = mag²/σ²(mag)
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   興味領域のバイナリマスク
  * `phase_offset::Bool = true`: フェーズオフセットをモデル化する (`true`)

### 戻り値

  * `typeof(similar(phas)){N-1}`: フェーズの(重み付き)最小二乗推定
  * [`typeof(similar(phas)){N-1}`]: フェーズオフセットの(重み付き)最小二乗推定   `phase_offset = true` の場合
