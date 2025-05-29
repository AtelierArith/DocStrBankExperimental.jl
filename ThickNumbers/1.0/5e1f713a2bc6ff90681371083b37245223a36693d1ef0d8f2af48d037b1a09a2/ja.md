```
loval(x::ThickNumber)
```

`x`の範囲の下限を表す値。`loval`は`ThickNumber`の任意のサブタイプによって実装されなければなりません。

# 例

```julia
julia> loval(Interval(1, 2))    # Interval{T} <: ThickNumber{T} と仮定
1
```
