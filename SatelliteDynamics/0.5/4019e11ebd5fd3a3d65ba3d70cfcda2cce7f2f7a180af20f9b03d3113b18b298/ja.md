モジュール全体のグローバル SpaceWeatherData。このデータオブジェクトは、明示的な SpaceWeatherData ファイルがそれらの変換に提供されていない場合、動的モデルによってジオ磁気データのデフォルトソースとして使用されます。

この値は、次のように自分のコードで上書きできます。

```julia
SatelliteDynamics.SpaceWeather.SPACE_WEATHER_DATA = SpaceWeatherData(index_file)
```

このグローバル変数のデフォルト値は、Celestrak Space Weather データリポジトリから取得されます: https://celestrak.org/SpaceData/
