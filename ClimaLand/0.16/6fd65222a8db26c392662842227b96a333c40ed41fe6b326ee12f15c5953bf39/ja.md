```
SoilSnowModel{FT}(;
    land_args::NamedTuple = (;),
    snow_model_type::Type{SnM},
    snow_args::NamedTuple = (;),
    soil_model_type::Type{SoM},
    soil_args::NamedTuple = (;),
    ) where {
        FT,
        SnM <: Snow.SnowModel{FT},
        SoM <: Soil.EnergyHydrology{FT},
        }
```

`LandHydrology`のコンストラクタは、具体的なモデルタイプと各コンポーネントに必要な引数を受け取り、それらのモデルを構築し、`SoilSnowModel`をそれらから構築します。

各コンポーネントモデルは、境界条件、ソース項、および相互作用項を含む、時間を進めるために必要なすべてのものを持って構築されます。
