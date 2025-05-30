```
Trapezoid!(turtle; length = 1.0, width = 1.0, ratio = 1.0, move = false, kwargs...)
```

タートルの前に台形を生成し、それをタートルに供給します。

## 引数

  * `turtle`: 台形を供給するタートル。
  * `length`: 台形の長さ。
  * `width`: 台形の底辺の幅。
  * `ratio`: 台形の上部と底辺の幅の比率。
  * `move`: タートルを前に移動させるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の各三角形に設定されるプロパティ。

## 詳細

台形を表す三角形メッシュが生成されます。台形はタートルの前に生成され、タートルの腕と頭の軸で定義された平面上に配置されます。引数 `length` はタートルの頭の軸に沿った台形の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、タートルは `length` に等しい距離だけ前に移動します。

## 戻り値

`nothing` を返しますが、サイドエフェクトとして `turtle` を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> Trapezoid!(turtle; length = 1.0, width = 1.0, ratio = 0.5);
```
