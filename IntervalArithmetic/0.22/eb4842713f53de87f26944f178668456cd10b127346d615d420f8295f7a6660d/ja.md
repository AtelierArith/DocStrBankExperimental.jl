```
pow(x, y)
```

`x`の正の実部の`y`乗を計算します。特に、`y`が薄い整数であっても、これは`pown(x, sup(y))`と同等ではありません。

IEEE標準1788-2015の`pow`関数を実装します（表9.1）。

参照: [`fastpow`](@ref), [`pown`](@ref) および [`fastpown`](@ref)。

# 例

```jldoctest
julia> setdisplay(:full);

julia> pow(bareinterval(2, 3), bareinterval(2))
BareInterval{Float64}(4.0, 9.0)

julia> pow(interval(-1, 1), interval(3))
Interval{Float64}(0.0, 1.0, trv)

julia> pow(interval(-1, 1), interval(-3))
Interval{Float64}(1.0, Inf, trv)
```
