```
coamoeba(f; alg=Greedy(), options...)
```

与えられたアルゴリズム `alg` を使用して `f` のコアモエバを計算します。使用できるアルゴリズムは次のとおりです。

  * `Greedy()`
  * `Coarse()`
  * `Simple()`

ただし、通常は `Greedy()` または `Coarse` を使用することをお勧めします。

コアモエバは $[0, 2π)^n$ に埋め込まれており、ここで $n$ は多項式に応じて 2 または 3 です。アルゴリズムは、この埋め込みを表すグリッド上でコアモエバを近似します。

## 例

```julia
@polyvar x y

# これは `Greedy()` アルゴリズムを使用します
coamoeba(x^2 + y^2 + 1)
```

## オプション引数

  * `resolution=600`: 明示的に渡されない場合のグリッドの解像度。
  * `membership_options=[MembershipTestOptions()](@ref)`: メンバーシップテストのオプション。
  * `test_domain`: 必要に応じてメンバーシップテストの開始値が引き出されるタプル `(xmin, xmax, ymin, ymax)` または `(xmin, xmax, ymin, ymax, zmin, zmax)`。
