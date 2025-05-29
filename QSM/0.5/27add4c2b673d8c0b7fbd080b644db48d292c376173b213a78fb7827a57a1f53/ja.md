```
multi_echo_average(
    phas::AbstractArray{<:AbstractFloat, N > 1};
    TEs::Union{Nothing, AbstractVector{<:Real}} = nothing,
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing,
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
) -> typeof(similar(phas)){N-1}
```

(重み付き) 平均値のマルチエコーデータ。

重み付き平均は次のように計算されます。

$$
\frac{\sum_{i=1}^{\#TEs} TE_i W_i phas_i}{\sum_{i=1}^{\#TEs} TE_i W_i}
$$

### 引数

  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: 展開されたマルチエコーフェーズ

### キーワード

  * `TEs::Union{Nothing, AbstractVector{<:Real}} = nothing`: エコー時間
  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing`: 重み
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`: 興味領域のバイナリマスク

### 戻り値

  * `typeof(similar(phas)){N-1}`: (重み付き) マルチエコーフェーズの平均値
