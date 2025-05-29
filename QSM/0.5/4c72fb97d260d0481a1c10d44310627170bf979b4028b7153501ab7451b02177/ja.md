```
multi_echo_linear_fit!(
    p::AbstractArray{<:AbstractFloat, N-1},
    phas::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}},
    mask::Union{Nothing, AbstractArray{Bool, N-1}},
) -> p
```

(重み付き) 最小二乗法によるマルチエコーデータのフィッティング (位相オフセット = 0)。

### 引数

  * `p::AbstractArray{<:AbstractFloat, N-1}`: (重み付き) 最小二乗法による位相の推定
  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: アンラップされたマルチエコー位相
  * `TEs::AbstractVector{<:Real}`: エコー時間
  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}}`: 重みの平方根、例えばボクセルの誤差分散の逆数 ~> W² = 1/σ²(phas) = mag²/σ²(mag)
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}}`: 興味領域のバイナリマスク

### 戻り値

  * `p`: (重み付き) 最小二乗法による位相の推定
