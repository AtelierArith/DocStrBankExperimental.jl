```
Erlang(α,θ)
```

*エルラン分布*は、整数形状パラメータを持つ[`Gamma`](@ref)分布の特別なケースです。

```julia
Erlang()       # 単位形状と単位スケールのエルラン分布、すなわちErlang(1, 1)
Erlang(a)      # 形状パラメータaと単位スケールのエルラン分布、すなわちErlang(a, 1)
Erlang(a, s)   # 形状パラメータaとスケールsのエルラン分布
```

外部リンク

  * [エルラン分布 - Wikipedia](http://en.wikipedia.org/wiki/Erlang_distribution)
