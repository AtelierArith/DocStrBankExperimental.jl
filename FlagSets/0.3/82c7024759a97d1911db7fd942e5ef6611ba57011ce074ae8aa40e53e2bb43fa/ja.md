```
flags(T)
```

型 `T` のフラグのセットを `Tuple` として返します。

# 例

```julia
julia> @flagset RoundingFlags RoundDown RoundUp RoundNearest

julia> flags(RoundingFlags)
(RoundingMode{:Down}(), RoundingMode{:Up}(), RoundingMode{:Nearest}())
```
