```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables,
    initial_conditions::SpeedyWeather.RossbyHaurwitzWave,
    model::SpeedyWeather.AbstractModel
)

```

ウィリアムソンらによる1992年のJ Computational Physicsにおけるロスビー・ハウルウィッツ波の初期条件で、渦度場の微小調和波をフィルタリングするための追加のカットオフ振幅 `c` を含みます。
