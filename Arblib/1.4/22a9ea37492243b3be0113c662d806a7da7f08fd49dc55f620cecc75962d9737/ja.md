```
setball(::Type{Arb}, m, r; prec = _precision(m))
```

`m` と `r` にそれぞれ設定された中点と半径を持つ `Arb` を返します。

`m` は `Arf` に変換されるため、丸められます。したがって、例えば `setball(1 // 3, 0)` は $1 / 3$ を含みません。

また、[`getball`](@ref) と [`add_error`](@ref) も参照してください。
