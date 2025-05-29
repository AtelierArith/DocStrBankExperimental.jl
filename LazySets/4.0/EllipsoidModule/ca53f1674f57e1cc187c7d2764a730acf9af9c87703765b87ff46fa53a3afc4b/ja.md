# 拡張ヘルプ

```
rand(::Type{Ellipsoid}; [N]::Type{<:AbstractFloat}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

中心は平均0、標準偏差1の正規分布に従うベクトルです。

形状行列のアイデアは[こちら](https://math.stackexchange.com/a/358092)から来ています。この行列は対称かつ正定値ですが、対角優位でもあります。

$$
Q =  \frac{1}{2}(S + S^T) + nI,
$$

ここで、$n$ = `dim`、$S$は係数が区間$[-1, 1]$で一様分布する$n × n$のランダム行列です。
