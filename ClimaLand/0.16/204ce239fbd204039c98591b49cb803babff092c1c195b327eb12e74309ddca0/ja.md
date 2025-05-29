```
LandHydrology{FT}(;
    land_args::NamedTuple = (;),
    soil_model_type::Type{SM},
    soil_args::NamedTuple = (;),
    surface_water_model_type::Type{SW},
    surface_water_args::NamedTuple = (;),
) where {
    FT,
    SM <: Soil.AbstractSoilModel{FT},
    SW <: Pond.AbstractSurfaceWaterModel{FT},
}
```

`LandHydrology`モデルのコンストラクタで、具体的なモデルタイプと各コンポーネントに必要な引数を受け取り、それらのモデルを構築し、それらから`LandHydrology`を構築します。

各コンポーネントモデルは、境界条件、ソース項、相互作用項を含む、時間を進めるために必要なすべてのものを持って構築されます。

パラメータや駆動大気データのような追加の引数は、`land_args`として渡されます。
