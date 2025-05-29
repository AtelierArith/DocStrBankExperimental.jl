```
multi_echo_average!(
    p::AbstractArray{<:AbstractFloat, N-1},
    phas::AbstractArray{<:AbstractFloat, N > 1},
    TEs::Union{Nothing, AbstractVector{<:Real}} = nothing,
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing,
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
) -> p
```

(重み付き) マルチエコーデータの平均。

重み付き平均は次のように計算されます。

$$
\frac{\sum_{i=1}^{\#TEs} TE_i W_i phas_i}{\sum_{i=1}^{\#TEs} TE_i W_i}
$$

### 引数

  * `p::AbstractArray{<:AbstractFloat, N-1}`: (重み付き) マルチエコーフェーズの平均
  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: アンラップされたマルチエコーフェーズ
  * `TEs::Union{Nothing, AbstractVector{<:Real}} = nothing`: エコー時間
  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing`: 重み
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味領域のバイナリマスク

### 戻り値

  * `p`: (重み付き) マルチエコーフェーズの平均

```
