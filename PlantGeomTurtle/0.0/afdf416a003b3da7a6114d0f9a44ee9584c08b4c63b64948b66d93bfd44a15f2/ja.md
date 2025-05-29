```
Triangle(turtle; length = 1.0, width = 1.0, move = false)
```

タートルの前に三角形を生成し、それを返します。

## 引数

  * `turtle`: 三角形を与えるタートル。
  * `length`: 三角形の長さ。
  * `width`: 三角形の幅。
  * `move`: タートルを前に進めるかどうか（`true` または `false`）。

## 詳細

三角形を表すメッシュが生成されます。三角形はタートルの腕と頭の軸で定義された平面上にタートルの前に生成されます。引数 `length` はタートルの頭の軸に沿った三角形の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、タートルは `length` に等しい距離だけ前に移動します。

## 返り値

三角形メッシュ（`Mesh` 型のオブジェクト）を返します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> t = Triangle(turtle; length = 2.0, width = 1.0);
```
