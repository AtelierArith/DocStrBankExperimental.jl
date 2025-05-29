```
@SLArray サイズ 名前
@SLArray 要素型 サイズ 名前
```

このマクロは、要素型 `ElType`、名前 `Names`、およびサイズ `Size` を持つラベル付き静的ベクトルを作成します。要素型が指定されていない場合、要素型はコンストラクタの引数から決定されます。

例えば：

```julia
ABCD = @SLArray (2, 2) (:a, :b, :c, :d)
x = ABCD(1.0, 2.5, 3.0, 5.0)
x.a == 1.0
x.b == 2.5
x.c == x[3]
x.d == x[2, 2]
EFG = @SLArray (2, 2) (e = 1:3, f = 4, g = 2:4)
y = EFG(1.0, 2.5, 3.0, 5.0)
EFG = @SLArray (2, 2) (e = (2, :), f = 4, g = 2:4)
```

ユーザーはインデックスを直接指定することもできます。

```julia
julia> EFG = @SLArray (2, 2) (e = 1:3, f = 4, g = 2:4);

julia> y = EFG(1.0, 2.5, 3.0, 5.0)
2×2 SLArray{Tuple{2,2},Float64,2,4,(e = 1:3, f = 4, g = 2:4)}:
 1.0  3.0
 2.5  5.0

julia> y.g
3-element view(reshape(::StaticArrays.SArray{Tuple{2,2},Float64,2,4}, 4), 2:4) with eltype Float64:
 2.5
 3.0
 5.0

julia> Arr = @SLArray (2, 2) (a = (2, :), b = 3);

julia> z = Arr(1, 2, 3, 4);

julia> z.a
2-element view(::StaticArrays.SArray{Tuple{2,2},Int64,2,4}, 2, :) with eltype Int64:
 2
 4
```
