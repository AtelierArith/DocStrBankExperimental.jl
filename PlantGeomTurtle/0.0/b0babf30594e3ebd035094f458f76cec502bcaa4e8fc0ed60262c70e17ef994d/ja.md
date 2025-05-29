```
Mesh(turtle, m::Mesh; scale = Vec(1.0, 1.0, 1.0), move = false)
```

タートルの状態を使用して、既存のメッシュをスケーリングします。

## 引数

  * `turtle`: メッシュを供給するタートル。
  * `m`: 標準の位置と向きの既存のスケールされていないメッシュ。
  * `scale`: x、y、z軸のスケーリングファクターを持つベクトル。
  * `move`: タートルを前に移動させるかどうか（`true` または `false`）。

## 詳細

既存のメッシュは（`scale`に従って）スケーリングされ、タートルと同じ方向に向くように回転し、タートルの前にメッシュが生成されるように平行移動されます。変換の前に元のメッシュのディープコピーが作成されます。

`move = true` の場合、タートルは `height` に等しい距離だけ前に移動します。

## 戻り値

三角形メッシュ（`Mesh` 型のオブジェクト）を返します。

## 例

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> e = PG.Ellipse();

julia> turtle = Turtle();

julia> ne = Mesh!(turtle, e, scale = PG.Vec(2.0, 2.0, 2.0));
```
