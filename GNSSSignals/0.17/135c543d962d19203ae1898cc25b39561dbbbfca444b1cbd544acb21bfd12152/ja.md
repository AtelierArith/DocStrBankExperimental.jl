```julia
get_code(system, phase, prn)

```

PRN `prn`のフェーズ`phase`でのタイプ <: `AbstractGNSS` のコードを取得します。

```julia-repl
julia> get_code(GPSL1(), 1200.3, 1)
```
