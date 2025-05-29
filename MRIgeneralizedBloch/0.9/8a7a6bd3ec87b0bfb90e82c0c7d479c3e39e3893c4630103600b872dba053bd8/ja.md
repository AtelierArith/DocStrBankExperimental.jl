```
greens_gaussian(κ)
```

ガウス線形に対応するグリーン関数を評価します。ここで `κ = (t-τ)/T2s` です。

# 例

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_gaussian((t-τ)/T2s)
1.9287498479639178e-22
```
