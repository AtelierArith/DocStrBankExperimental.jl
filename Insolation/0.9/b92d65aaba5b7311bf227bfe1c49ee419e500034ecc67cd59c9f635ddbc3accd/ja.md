```
daily_zenith_angle(date::DateTime,
                   data0::DateTime,
                   od::OrbitalData,
                   latitude::FT,
                   param_set::IP.AIP;
                   eot_correction::Bool=true,
                   milankovitch::Bool=true) where {FT <: Real}
```

特定の緯度における日付に基づく日平均の入射日射量と地球-太陽距離に対応する有効天頂角を返します。

`param_set` は ClimaParams.jl の AbstractParameterSet です。

`eot_correction` はオプションのブール型キーワード引数で、デフォルトは true です。true に設定すると、時間の方程式補正がオンになります。このスイッチ機能は、再解析との簡単な比較のために実装されています。

`milankovitch` はオプションのブール型キーワード引数で、デフォルトは true です。true に設定すると、指定された DateTime に対して軌道パラメータが計算され、false に設定すると、ClimaParams の J2000 紀元の軌道パラメータが使用されます。
