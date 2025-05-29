```
Biogeochemistry(underlying_biogeochemistry;
                light_attenuation = nothing,
                sediment = nothing,
                particles = nothing,
                modifiers = nothing)
```

`underlying_biogeochemistry`に基づいて、`light_attenuation`モデル、`sediment`、`particles`、および`modifiers`を持つ生物地球化学モデルを構築します。

# キーワード引数

  * `light_attenuation_model`: 利用可能な光の減衰を統合した光減衰モデル
  * `sediment_model`: `AbstractSediment`のスロット
  * `particles`: `BiogeochemicalParticles`のスロット
  * `modifiers`: 傾向が計算された後や状態が更新されたときに生物地球化学を修正するコンポーネントのスロット
