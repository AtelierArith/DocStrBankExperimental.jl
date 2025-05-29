```
namedaxes(img) -> NamedTuple{names}(axes)
```

`NamedTuple`を返します。ここで、名前は次元の名前であり、各インデックスは対応する次元の軸です。`x`に対して`HasDimNames`が定義されていない場合、デフォルトの名前が返されます。`x`は`axes`メソッドを持っている必要があります。

```jldoctest; setup = :(using ImageCore)
julia> img = reshape(1:24, 2,3,4);

julia> namedaxes(img)
(dim_1 = Base.OneTo(2), dim_2 = Base.OneTo(3), dim_3 = Base.OneTo(4))
```
