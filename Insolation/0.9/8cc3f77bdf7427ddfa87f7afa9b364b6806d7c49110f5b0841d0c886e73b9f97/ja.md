```
solar_flux_and_cos_sza(date::DateTime,
                  date0::DateTime,
                  od::OrbitalData,
                  longitude::FT,
                  latitude::FT,
                  param_set::IP.AIP) where {FT <: Real}
```

大気上端（TOA）太陽フラックス、すなわち地球-太陽距離とcos（太陽天頂角）で重み付けされた総太陽放射（TSI）を返します。これはRRTMGP.jlへの入力です。param_setはClimaParams.jlからのAbstractParameterSetです。
