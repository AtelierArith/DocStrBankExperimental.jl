```
BoundaryFunction(fun; discrete=false, parameters=nothing, reduce_dims=true)
```

境界条件をフィールドに定義するために使用できる「境界関数」オブジェクトを作成します。

## 引数

  * `fun`: 境界条件を定義する関数。
  * `discrete=false`: `true`の場合、境界関数は離散的で、署名は `f(grid, loc, dim, inds...)` です。
  * `parameters=nothing`: 境界関数に渡されるオプションのパラメータ。
  * `reduce_dims=true`: `true`の場合、境界関数は操作する次元の数を減らします。`false`の場合、関数はインデックスの数と同じ数の座標を受け入れます。

## 使用法

以下の例は、2Dグリッドの境界で放物線プロファイルを初期化するために境界関数を使用する方法を示しています。

```julia
using Chmy

arch = Arch(CPU())
grid = UniformGrid(arch; origin=(0, 0), extent=(2, 2), dims=(10, 10))

f = Field(arch, grid, Center())
xbc = BoundaryFunction((x, ly) -> x * (ly - x); parameters=(2.0, ))

bc!(arch, grid, f => (x = Dirichlet(xbc), y = Neumann()))
```
