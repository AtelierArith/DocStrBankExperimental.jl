```
group([keyf=identity], X; [restype=Dictionary])
```

`X`の要素を`keyf(x)`でグループ化し、各グループの`x`値のリストに対する`keyf(x)`値のマッピングを返します。

結果はデフォルトで（順序付きの）`Dictionary`ですが、基本の`Dict`として指定することもできます。

辞書の代わりに、`restype=KeyedArray`（`AxisKeys.jl`から）を指定すると、`KeyedArray`が得られます。その`axiskeys`はグループキーです。

# 例

```julia
xs = 3 .* [1, 2, 3, 4, 5]
g = group(isodd, xs)
g == dictionary([true => [3, 9, 15], false => [6, 12]])


g = group(x -> (a=isodd(x),), xs; restype=KeyedArray)
g == KeyedArray([[6, 12], [3, 9, 15]]; a=[false, true])
```
