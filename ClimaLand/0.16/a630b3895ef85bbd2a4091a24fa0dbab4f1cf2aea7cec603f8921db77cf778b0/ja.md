```
LandModel{FT}(;
    soilco2_type::Type{MM},
    soilco2_args::NamedTuple = (;),
    land_args::NamedTuple = (;),
    soil_model_type::Type{SM},
    soil_args::NamedTuple = (;),
    canopy_component_types::NamedTuple = (;),
    canopy_component_args::NamedTuple = (;),
    canopy_model_args::NamedTuple = (;),
    snow_model_type::Type{SnM},
    snow_args::NamedTuple = (;),
    ) where {
        FT,
        SM <: Soil.EnergyHydrology{FT},
        MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
        SnM <: Snow.SnowModel{FT}
        }
```

`LandModel`のコンストラクタで、具体的なモデルタイプと各コンポーネントに必要な引数を受け取り、それらのモデルを構築し、それらから`LandModel`を構築します。

各コンポーネントモデルは、境界条件、ソース項、および相互作用項を含む、時間を進めるために必要なすべてのものを持って構築されます。
