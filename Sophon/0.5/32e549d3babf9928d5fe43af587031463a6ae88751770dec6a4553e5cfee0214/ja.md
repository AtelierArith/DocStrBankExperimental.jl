```
FourierFeature(in_dims::Int, std::NTuple{N,Pair{S,T}}) where {N,S,T<:Int}
FourierFeature(in_dims::Int, frequencies::NTuple{N, T}) where {N, T <: Real}
FourierFeature(in_dims::Int, out_dims::Int, std::Real)
```

フーリエ特徴ネットワーク。

# 引数

  * `in_dims`: 入力次元の数。
  * `std`: `sigma => out_dims` のペアのタプルで、`sigma` はガウス分布の標準偏差です。

$$
\phi^{(i)}(x)=\left[\sin \left(2 \pi W^{(i)} x\right) ; \cos 2 \pi W^{(i)} x\right],\ W^{(i)} \sim \mathcal{N}\left(0, \sigma^{(i)}\right),\ i\in 1, \dots, D
$$

  * `frequencies`: 周波数のタプル $(f1,f2,...,fn)$。

$$
\phi^{(i)}(x)=\left[\sin \left(2 \pi f_i x\right) ; \cos 2 \pi f_i x\right]
$$

# パラメータ

`std` が使用される場合、パラメータは式中の `W` です。

# 入力

  * `x`: `AbstractArray` で `size(x, 1) == in_dims`。

# 戻り値

  * $$
    [\phi^{(1)}, \phi^{(2)}, ... ,\phi^{(D)}]
    $$

    で `size(y, 1) == sum(last(modes) * 2)`。

# 例

```julia
julia> f = FourierFeature(2,10,1) # ランダムフーリエ特徴
FourierFeature(2 => 10)

julia> f = FourierFeature(2, (1 => 3, 50 => 4)) # マルチスケールランダムフーリエ特徴
FourierFeature(2 => 14)

julia>  f = FourierFeature(2, (1,2,3,4)) # 事前定義された周波数
FourierFeature(2 => 16)
```

# 参考文献

[rahimi2007random](@cite)

[tancik2020fourier](@cite)

[wang2021eigenvector](@cite)
