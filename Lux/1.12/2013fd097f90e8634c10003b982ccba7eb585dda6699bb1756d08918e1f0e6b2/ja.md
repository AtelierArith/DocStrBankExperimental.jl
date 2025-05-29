```
bf16(m)
```

`m`の*浮動小数点*値の`eltype`を`BFloat16`に変換します。構造体への再帰を避けるために、`Functors.@leaf`でマークしてください。

!!! warning
    この関数を使用する前に`BFloat16s.jl`をロードする必要があります。


!!! tip "Support for `BFloat16`"
    ほとんどのLux操作はまだ`BFloat16`に最適化されていません。代わりに、これは`Reactant.@compile`と一緒に使用することを意図しています。

