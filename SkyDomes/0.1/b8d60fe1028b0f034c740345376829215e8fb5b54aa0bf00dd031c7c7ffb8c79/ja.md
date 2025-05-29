```
radiosity(m::UniformSky, sky::SkySectors, Idif::SVector{nw, Float64}) where nw
```

均一空のモデルを仮定して、水平面上の各セクションの放射輝度を計算します。水平面上の拡散放射照度（`Idif`、`nw` 波長帯を持つ）を考慮します。詳細についてはパッケージのドキュメントを参照してください。
