```julia
add!(
    D::Dict{Symbol, SpeedyWeather.AbstractOutputVariable},
    outputvariables::SpeedyWeather.AbstractOutputVariable...
) -> Dict{Symbol, SpeedyWeather.AbstractOutputVariable}

```

`outputvariables`をNetCDF出力の対象となる変数を定義する辞書に追加します。
