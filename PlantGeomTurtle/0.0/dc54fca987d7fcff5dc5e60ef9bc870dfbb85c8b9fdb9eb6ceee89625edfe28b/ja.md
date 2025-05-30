```
Triangle!(turtle; length = 1.0, width = 1.0, move = false, kwargs...)
```

タートルの前に三角形を生成し、それをタートルに供給します。

## 引数

  * `turtle`: 三角形を供給するタートル。
  * `length`: 三角形の長さ。
  * `width`: 三角形の幅。
  * `move`: タートルを前に移動させるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の各三角形に設定されるプロパティ。

## 詳細

三角形を表す三角形メッシュが生成されます。三角形はタートルの腕と頭の軸で定義された平面上で、タートルの前に生成されます。引数 `length` はタートルの頭の軸に沿った三角形の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、タートルは `length` に等しい距離だけ前に移動します。

## 返り値

`nothing` を返しますが、サイドエフェクトとして `turtle` を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> Triangle!(turtle; length = 2.0, width = 1.0);
```
