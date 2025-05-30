```
SolidFrustum!(turtle; length = 1.0, width = 1.0, height = 1.0, n = 80, move = false, kwargs...)
```

タートルの前にソリッドフラスコを生成し、それをタートルに供給します。

## 引数

  * `turtle`: ソリッドフラスコを供給するタートル。
  * `length`: ソリッドフラスコの基底にある楕円の長さ。
  * `width`: ソリッドフラスコの基底にある楕円の幅。
  * `height`: ソリッドフラスコの高さ。
  * `n`: メッシュ内の三角形の数（偶数でなければならない）。
  * `move`: タートルを前に移動させるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の三角形ごとに設定されるプロパティ。

## 詳細

n個の三角形で構成されるメッシュが生成され、ソリッドフラスコを近似します。フラスコはタートルの前に生成され、基底はタートルの腕と上の軸で定義された平面上にあり、頭の軸を中心にします。`length`引数は上の軸を指し、`width`は腕の軸を指し、`height`は頭の軸に関連しています。

`move = true`の場合、タートルは`height`に等しい距離だけ前に移動します。

## 返り値

`nothing`を返しますが、サイドエフェクトとして`turtle`を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> SolidFrustum!(turtle; length = 1.0, width = 1.0, height = 2.0, n = 80);
```
