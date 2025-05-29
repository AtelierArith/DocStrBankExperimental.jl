```
make_update_boundary_fluxes(
    land::LandModel{FT, MM, SM, RM, SnM},
) where {
    FT,
    MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
    SM <: Soil.RichardsModel{FT},
    RM <: Canopy.CanopyModel{FT}
    SnM <: Snow.SnowModel{FT}
    }
```

関数を作成するメソッド; 返される関数は、統合モデルの追加の補助変数を更新し、すべてのコンポーネントモデルの境界補助変数も更新します。

この関数は、傾向関数の評価の前に、各ode関数評価ごとに呼び出されます。
