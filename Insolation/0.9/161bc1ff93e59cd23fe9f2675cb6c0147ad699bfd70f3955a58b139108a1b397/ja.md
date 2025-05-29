```
insolation(θ::FT, d::FT, param_set::IP.AIP) where {FT <: Real}
```

天頂角と地球-太陽距離を考慮して日射量を返します。param_setはClimaParams.jlのAbstractParameterSetです。
