```
hival(x::ThickNumber)
```

`x`の範囲の上限を表す値。`hival`は`ThickNumber`の任意のサブタイプによって実装されなければなりません。

# 例

```julia
julia> hival(Interval(1, 2))    # Interval{T} <: ThickNumber{T} と仮定
2
```
