```
Rectangle!(turtle; length = 1.0, width = 1.0, move = false, kwargs...)
```

タートルの前に長方形を生成し、それをタートルに供給します。

## 引数

  * `turtle`: 長方形を供給するタートル。
  * `length`: 長方形の長さ。
  * `width`: 長方形の幅。
  * `move`: タートルを前に進めるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の三角形ごとに設定されるプロパティ。

## 詳細

長方形を表す三角形メッシュが生成されます。長方形はタートルの前に、タートルの腕と頭の軸で定義された平面上に生成されます。引数 `length` はタートルの頭の軸に沿った長方形の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、タートルは `length` に等しい距離だけ前に移動します。

## 戻り値

`nothing` を返しますが、サイドエフェクトとして `turtle` を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> Rectangle!(turtle; length = 1.0, width = 0.5);
```
