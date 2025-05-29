```
Metabolite(name::String, commonname::Union{Missing, String}, mz::Union{Missing, Float64}, rt::Union{Missing, Float64}) <: AbstractFeature
Metabolite(name::String)
```

LCMSからの小分子代謝物を表します。フィールドは次のとおりです。

  * `name`: 必須、これは一意の識別子である必要があります
  * `commonname`: "プロピオン酸"のような化学名を指す場合があります
  * `mz`: 質量/電荷比
  * `rt`: 保持時間
