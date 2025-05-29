AquaPlanetの海面温度は、時間と経度で一定ですが、緯度に応じてcoslat²に従って変化します。次のように作成されます。

```
ocean = AquaPlanet(spectral_grid, temp_equator=302, temp_poles=273)
```

フィールドとオプションは次のとおりです。

  * `temp_equator::Any`: [OPTION] 赤道での温度 [K]
  * `temp_poles::Any`: [OPTION] 極での温度 [K]
