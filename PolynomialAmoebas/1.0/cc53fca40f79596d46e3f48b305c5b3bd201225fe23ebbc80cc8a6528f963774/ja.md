```
imaginary_projection(f; alg=Greedy(), grid=..., options...)
```

与えられたアルゴリズム `alg` と 2D または 3D グリッドを使用して `f` の imaginary_projection を計算します。`alg` は次のいずれかです。

  * `Greedy()`
  * `Simple()`

しかし、おそらく `Greedy()` のみを使用したいでしょう。

## 例

```julia
@polyvar x y

g = x^4 + im * x^3 - x^2 * y^2 + 3x^3 - 2im*x*y^2 + (4-2im)*x + 0.5*y^2 + 1.5
grid = Grid2D(xlims=(-4, 4), ylims=(-5, 5), res=(1200, 1200))
# これは `Greedy()` アルゴリズムを使用します
imaginary_projection(g, grid=grid)
```

これらのアルゴリズムはすべて、グリッドに基づく imaginary projection 𝐼(𝑓) の近似です。これは基本的に異なるグリッドポイントに対するメンバーシップテストを適用します。グリッドは明示的に渡すことができますが、そうでない場合はヒューリスティックに基づいて計算されます。

  * `membership_options=[MembershipTestOptions()](@ref)`: メンバーシップテストのオプション。
  * `npasses=1`: `Greedy()` アルゴリズムは、品質を向上させるために複数回のパスを行うことができます。
  * `test_domain`: メンバーシップテストの開始値が引き出されるタプル `(xmin, xmax, ymin, ymax, [zmin, zmax])`。
