```
Extrema(T::Type = Float64)
Extrema(min_init::T, max_init::T)
```

データストリームの最大値と最小値（およびそれぞれの出現回数）をタイプ `T` に対して取得します。

# 例

```
Extrema(Float64) == Extrema(Inf, -Inf)

o = fit!(Extrema(), rand(10^5))
extrema(o)
maximum(o)
minimum(o)
```
