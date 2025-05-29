```
stripscalar(x)
```

値 `x` をデリファレンスします。

もし `x` がスカラーのようなオブジェクト（0次元配列や `Ref` のような）であれば、`stripscalar` はその内部の値を返します。それ以外の場合、`x` は変更されずに返されます。

0次元配列のセマンティクス（存在する場合）を持つ形状付きスカラーのようなビューを取り除くのに便利ですが、配列のようなビューは変更されません。

例:

```julia
data = [1, 2, 3]
shape1 = NamedTupleShape(a = ScalarShape{Real}(), b = ArrayShape{Real}(2))
x1 = shape1(data)
@assert x1 isa NamedTuple

shape2 = ArrayShape{Real}(3)
x2 = shape2(data)
@assert x2 isa AbstractArray{Int,1}
```
