```
struct ScalarField{VF,M<:AbstractMesh,BC} <: AbstractScalarField
    values::VF  # セル中心のスカラー値
    mesh::M     # メッシュへの参照
    BCs::BC     # ユーザー提供の境界条件を格納
end
```
