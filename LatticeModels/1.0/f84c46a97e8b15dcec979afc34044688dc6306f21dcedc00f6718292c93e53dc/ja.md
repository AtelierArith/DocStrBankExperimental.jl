```
setboundaries(lat, boundaries...[; checkboundaries=true, rmdup=false])
```

格子 `lat` の境界条件を設定します。

## 引数

  * `lat`: 格子。
  * `boundaries`: 境界条件。単一の `Boundary` または `Boundary` オブジェクトの `Tuple` であることができます。

## キーワード引数

  * `checkboundaries`: `true` の場合、境界条件が格子サイト内で重なっているかどうかを確認します。
  * `rmdup`: `true` の場合、格子から重複するサイトを削除します。

## 例

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(4, 4);

julia> l2 = setboundaries(l, [4, 0] => true, [0, 4] => pi);

julia> l2.boundaries
Boundary conditions (depth = 1):
  Bravais[4, 0] → periodic
  Bravais[0, 4] → twist θ = 3.14
```
