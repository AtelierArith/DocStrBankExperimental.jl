```
Trapezoid(turtle; length = 1.0, width = 1.0, ratio = 1.0, move = false)
```

タートルの前に台形を生成し、それを返します。

## 引数

  * `turtle`: 台形を与えるタートル。
  * `length`: 台形の長さ。
  * `width`: 台形の底辺の幅。
  * `ratio`: 台形の上辺と底辺の幅の比率。
  * `move`: タートルを前に進めるかどうか（`true` または `false`）。

## 詳細

台形を表す三角形メッシュが生成されます。台形はタートルの前に、タートルの腕と頭の軸で定義された平面上に生成されます。引数 `length` はタートルの頭の軸に沿った台形の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、タートルは `length` に等しい距離だけ前に移動します。

## 返り値

三角形メッシュ（型 `Mesh` のオブジェクト）を返します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> t = Trapezoid(turtle; length = 1.0, width = 1.0, ratio = 0.5);
```
