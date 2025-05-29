```
plate(size, conditions...)
```

WellPlateを構築し、そのサイズと条件を指定します。

# 例

```julia-repl
julia> plate(96, cellline = :Raji)
96ウェルのプレート、8行12列
条件: [:cellline]
```

[`WellPlate`](@ref)も参照してください。
