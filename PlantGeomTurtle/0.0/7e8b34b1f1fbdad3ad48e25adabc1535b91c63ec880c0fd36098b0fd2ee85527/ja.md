```
HollowCylinder(turtle; length = 1.0, width = 1.0, height = 1.0, n = 40, move = false)
```

亀の前に中空の円柱を生成し、それを返します。

## 引数

  * `turtle`: 中空の円柱を与える亀。
  * `length`: 中空の円柱の基底にある楕円の長さ。
  * `width`: 中空の円柱の基底にある楕円の幅。
  * `height`: 中空の円柱の高さ。
  * `n`: メッシュ内の三角形の数（偶数でなければならない）。
  * `move`: 亀を前に移動させるかどうか（`true` または `false`）。

## 詳細

n個の三角形で構成されるメッシュが生成され、中空の円柱を近似します。円柱は亀の前に生成され、基底は亀の腕と上の軸で定義された平面上にあり、頭の軸を中心にします。`length` 引数は上の軸を指し、`width` は腕の軸を指し、`height` は頭の軸に関連しています。

`move = true` の場合、亀は `height` に等しい距離だけ前に移動します。

## 戻り値

三角形メッシュ（`Mesh` 型のオブジェクト）を返します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> c = HollowCylinder(turtle; length = 1.0, width = 1.0, height = 2.0, n = 40);
```
