```
HollowCube(turtle; length = 1.0, width = 1.0, height = 1.0, move = false)
```

亀の前に中空の立方体を生成し、それを返します。

## 引数

  * `turtle`: 中空の立方体を与える亀。
  * `length`: 中空の立方体の基底にある長方形の長さ。
  * `width`: 中空の立方体の基底にある長方形の幅。
  * `height`: 中空の立方体の高さ。
  * `move`: 亀を前に進めるかどうか（`true` または `false`）。

## 詳細

中空の立方体のメッシュが生成されます。立方体は亀の前に生成され、基底は亀の腕と上の軸によって定義された平面上にあり、頭の軸を中心にします。`length` 引数は上の軸を指し、`width` は腕の軸を指し、`height` は頭の軸に関連しています。

`move = true` の場合、亀は `height` に等しい距離だけ前に移動します。

## 返り値

三角形メッシュ（`Mesh` 型のオブジェクト）を返します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> c = HollowCube(turtle; length = 1.0, width = 1.0, height = 2.0);
```
