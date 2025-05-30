```
HollowFrustum!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 40, move = false, kwargs...)
```

亀の前に中空の円錐台を生成し、それを亀に供給します。

## 引数

  * `turtle`: 中空の円錐台を供給する亀。
  * `length`: 中空の円錐台の底にある楕円の長さ。
  * `width`: 中空の円錐台の底にある楕円の幅。
  * `height`: 中空の円錐台の高さ。
  * `n`: メッシュ内の三角形の数（偶数でなければならない）。
  * `move`: 亀を前に移動させるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の三角形ごとに設定されるプロパティ。

## 詳細

中空の円錐台を近似する n 個の三角形を持つメッシュが生成されます。円錐台は亀の前に生成され、亀の腕と上の軸によって定義された平面上に基づき、頭の軸を中心に配置されます。`length` 引数は上の軸を指し、`width` は腕の軸を指し、`height` は頭の軸に関連しています。

`move = true` の場合、亀は `height` に等しい距離だけ前に移動します。

## 戻り値

`nothing` を返しますが、副作用として `turtle` を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> HollowFrustum!(turtle; length = 1.0, width = 1.0, height = 2.0, n = 40);
```
