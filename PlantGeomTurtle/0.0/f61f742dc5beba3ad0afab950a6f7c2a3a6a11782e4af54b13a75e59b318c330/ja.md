```
SolidCube!(turtle; length = 1.0, width = 1.0, height = 1.0, move = false, kwargs...)
```

タートルの前にソリッドキューブを生成し、それをタートルに供給します。

## 引数

  * `turtle`: ソリッドキューブを供給するタートル。
  * `length`: ソリッドキューブの基底にある長方形の長さ。
  * `width`: ソリッドキューブの基底にある長方形の幅。
  * `height`: ソリッドキューブの高さ。
  * `move`: タートルを前に移動させるかどうか（`true` または `false`）。
  * `kwargs`: メッシュ内の三角形ごとに設定されるプロパティ。

## 詳細

ソリッドキューブのメッシュが生成されます。キューブはタートルの前に生成され、基底はタートルのアームと上の軸で定義された平面上にあり、頭の軸を中心にします。`length` 引数は上の軸を指し、`width` はアームの軸を指し、`height` は頭の軸に関連しています。

`move = true` の場合、タートルは `height` に等しい距離だけ前に移動します。

## 戻り値

`nothing` を返しますが、サイドエフェクトとして `turtle` を変更します。

## 例

```jldoctest
julia> turtle = Turtle();

julia> SolidCube!(turtle; length = 1.0, width = 1.0, height = 2.0);
```
