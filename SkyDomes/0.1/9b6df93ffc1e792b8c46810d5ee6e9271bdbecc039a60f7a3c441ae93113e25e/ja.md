```
radiosity(m::StandardSky, sky::SkySectors, Idif::SVector{nw, Float64})
```

標準空のモデルを仮定し、`nw` 波長帯に対して水平面上の拡散放射照度 (`Idif`、`nw` 波長帯を持つ) に基づいて、水平面上の `sky` の各セクションの放射照度を計算します。詳細についてはパッケージのドキュメントを参照してください。
