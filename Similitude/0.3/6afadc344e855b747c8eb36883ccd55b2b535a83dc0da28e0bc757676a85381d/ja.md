```
(U::UnitSystem)(v::Number, d) ↦ Quantity(U,v,d) = Quantity{U}(v,d)
```

数値 `Quantity` は、`U::UnitSystem` で指定された次元 `d` を持つ値 `v` を持っています。

```Julia
julia> Metric(1,energy)
1 [J] Metric

julia> English(1,energy)
1 [lbf⋅ft] English
```

代替構文 `Quantity(U::UnitSystem, v::Number, d)` も標準構文として利用可能です。`using UnitSystems` の代わりに `using Similitude` を使用する場合、この同じ構文はコードを変更することなく出力を生成できるように書くことができます。
