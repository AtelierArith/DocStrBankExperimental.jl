```
minimum_finite([f=identity], A; kwargs...)
```

`Inf`や`NaN`などの有限でない値を無視しながら、`minimum(f, A)`を計算します。

`A`が複数のチャネルを持つカラント配列（例：`Array{RGB}`）の場合、`min`の比較はチャネルごとに行われます。

サポートされている`kwargs`は`minimum(f, A; kwargs...)`のものです。
