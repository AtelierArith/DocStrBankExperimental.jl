```
instantaneous_zenith_angle(
    d::FT,
    δ::FT,
    η_UTC::FT,
    longitude::FT,
    latitude::FT,
) where {FT}
```

特定の経度（度）と緯度（度）での天頂角（ラジアン）、方位角（ラジアン）、および地球-太陽距離（m）を返します。これは、地球-太陽距離（m）、偏角（ラジアン）、および0ᵒ経度での時間角（ラジアン）を考慮したものです。
