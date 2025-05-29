```
pown(x, n)
```

IEEE標準1788-2015（表9.1）の`pown`関数を実装します。

参照: [`fastpown`](@ref), [`pow`](@ref) および [`fastpow`](@ref)。

# 例

```jldoctest
julia> setdisplay(:full);

julia> pown(bareinterval(2, 3), 2)
BareInterval{Float64}(4.0, 9.0)

julia> pown(interval(-1, 1), 3)
Interval{Float64}(-1.0, 1.0, com)

julia> pown(interval(-1, 1), -3)
Interval{Float64}(-Inf, Inf, trv)
```
