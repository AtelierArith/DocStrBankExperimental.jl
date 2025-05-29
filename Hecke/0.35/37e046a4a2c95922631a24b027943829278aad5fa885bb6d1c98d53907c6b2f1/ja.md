```
MapFromFunc(D, C, f, [g])
```

呼び出し可能なオブジェクト `f` を与えられたとき、マップ `D -> C, x -> f(x)` を作成します。`g` が提供される場合、それは `f(g(x)) = x` を満たすと仮定され、逆像関数として使用されます。

# 例

```jldoctest
julia> F = GF(2);

julia> f = MapFromFunc(QQ, F, x -> F(numerator(x)) * inv(F(denominator(x))))
julia関数によって定義されたマップ
  有理体から
  特性2の素体へ

julia> f(QQ(1//3))
1

julia> println(f)
マップ: QQ -> F

julia> f = MapFromFunc(QQ, F, x -> F(numerator(x)) * inv(F(denominator(x))), y -> QQ(lift(ZZ, y)),)
逆を持つjulia関数によって定義されたマップ
  有理体から
  特性2の素体へ

julia> preimage(f, F(1))
1

julia> println(f)
マップ: QQ -> F

```
