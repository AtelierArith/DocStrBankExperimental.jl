```
@ri_str -> RealInterval
```

数学的実数区間表記を用いて `RealInterval` を作成します。

# 例

```julia
julia> interval = ri"[4, 7)";

julia> 4 in interval
true

julia> 7 in interval
false
```
