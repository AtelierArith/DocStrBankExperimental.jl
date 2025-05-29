```
fourier_attenuation(f::Vector{S}, r::T, ane::AnelasticAttenuationParameters{U,V}, site::SiteParameters{W}) where {S<:Float64,T<:Real,U<:Real,V<:Real,W<:Real}
```

周波数 `f` に対する `Q(f)` 効果と `κ0` フィルターを含む、結合された全経路減衰。距離は、`ane.rmetric` で定義されたメトリックに応じて、等価点源距離 `r_ps` または破裂距離 `r_rup` の観点から定義されます。
