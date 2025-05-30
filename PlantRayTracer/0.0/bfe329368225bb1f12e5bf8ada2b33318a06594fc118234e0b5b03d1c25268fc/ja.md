```
LambertianSource(x, y, z)
LambertianSource(axes)
```

ローカル座標系を与えられた3つの別々の`Vec`オブジェクト（x, y, z）または3つの軸を含むタプルとして、ラバルティアン放射源の角度を作成します。光線は、`z`方向で定義された半球に向けて生成されます。放射源に関する詳細はVPLドキュメントを参照してください。

## 例

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_dir = LambertianSource(PG.X(), PG.Y(), PG.Z());

julia> source_dir = LambertianSource((PG.X(), PG.Y(), PG.Z()));
```
