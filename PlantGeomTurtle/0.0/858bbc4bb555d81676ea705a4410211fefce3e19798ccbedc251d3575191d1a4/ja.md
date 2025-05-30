```
SolidCone!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 40, move = false, kwargs...)
```

亀の前にソリッドフラスコを生成し、それを亀に供給します。

## 引数

  * `turtle`: ソリッドコーンを供給する亀。
  * `length`: ソリッドコーンの基底にある楕円の長さ。
  * `width`: ソリッドコーンの基底にある楕円の幅。
  * `height`: ソリッドコーンの高さ。
  * `n`: メッシュ内の三角形の数（偶数でなければならない）。
  * `move`: 亀を前に移動させるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の三角形ごとに設定されるプロパティ。

## 詳細

n個の三角形で構成されるメッシュが生成され、ソリッドコーンを近似します。コーンは亀の前に生成され、基底は亀の腕と上の軸で定義された平面上にあり、頭の軸を中心にします。`length`引数は上の軸を指し、`width`は腕の軸を指し、`height`は頭の軸に関連しています。

`move = true`の場合、亀は`height`に等しい距離だけ前に移動します。

## 戻り値

`nothing`を返しますが、亀を副作用として変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> SolidCone!(turtle; length = 1.0, width = 1.0, height = 2.0, n = 40);
```
