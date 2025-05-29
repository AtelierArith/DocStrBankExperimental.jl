```
combined_kappa_frequency(r::T, Af2target::Float64, ane::AnelasticAttenuationParameters, site::SiteParameters) where T<:Real
```

結合されたκ*rおよびκ*0フィルター（平方バージョン）が`Af2target`の値を与える周波数。`r`は、`ane.rmetric`に一致するものに応じて、`r_ps`または`r_rup`のいずれかになります。
