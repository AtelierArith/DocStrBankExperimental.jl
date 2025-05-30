```
Triangle!(turtle; length = 1.0, width = 1.0, move = false, kwargs...)
```

亀の前に三角形を生成し、それを亀に与えます。

## 引数

  * `turtle`: 三角形を与える亀。
  * `length`: 三角形の長さ。
  * `width`: 三角形の幅。
  * `move`: 亀を前に進めるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の各三角形に設定されるプロパティ。

## 詳細

三角形を表す三角形メッシュが生成されます。三角形は亀の前に、亀の腕と頭の軸で定義された平面上に生成されます。引数 `length` は亀の頭の軸に沿った三角形の軸を指し、`width` は直交する軸を指します。

`move = true` の場合、亀は `length` に等しい距離だけ前に移動します。

## 返り値

`nothing` を返しますが、亀を副作用として変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> Triangle!(turtle; length = 2.0, width = 1.0);
```
