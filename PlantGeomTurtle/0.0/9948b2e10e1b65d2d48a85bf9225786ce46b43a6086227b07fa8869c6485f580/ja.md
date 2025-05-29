```
Ellipse!(turtle; length = 1.0, width = 1.0, n = 20, move = false, kwargs...)
```

タートルの前に楕円を生成し、それをタートルに供給します。

## 引数

  * `turtle`: 楕円を供給するタートル。
  * `length`: 楕円の長さ。
  * `width`: 楕円の幅。
  * `n`: 楕円を近似するメッシュの三角形の数（整数）。
  * `move`: タートルを前に進めるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の各三角形に設定されるプロパティ。

## 詳細

`n` 個の三角形を持つ三角形メッシュが生成され、楕円を近似します。楕円はタートルの前に生成され、タートルの腕と頭の軸で定義された平面上に配置されます。引数 `length` はタートルの頭の軸に沿った楕円の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、タートルは `length` に等しい距離だけ前に移動します。

## 戻り値

`nothing` を返しますが、サイドエフェクトとして `turtle` を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> Ellipse!(turtle; length = 1.0, width = 0.5, n = 40);
```
