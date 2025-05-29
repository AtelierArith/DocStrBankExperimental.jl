```
linkparameters(latlon::LatLon, f::Real, p::Real, θ::Real, D::Real; η::Real=60.0, hs::Union{Real,Missing}=missing, polarization::IturEnum=EnumCircularPolarization)
```

リンクバジェットのためのリンクパラメータ。雲、気体、雨、散乱、および総減衰を含む; 宇宙ステーションのノイズ温度、地球局のノイズ温度、および交差偏波識別。

# 引数

  * `latlon::LatLon`: 緯度と経度（度）
  * `f::Real`: 周波数（GHz）
  * `p::Real`: 超過確率（%）
  * `θ::Real`: 仰角（度）
  * `D::Real`: アンテナ直径（m）
  * `η::Real=60`: アンテナ効率（% 0から100の範囲、通常は60）
  * `hs::Union{Real,Missing}=missing`: 地上局の高度（km）
  * `polarization::IturEnum=EnumCircularPolarization`: 偏波（EnumHorizontalPolarization、EnumVerticalPolarization、またはEnumCircularPolarization）

# 戻り値

  * `(Ac=Ac, Ag=Ag, Ar=Ar, As=As, At=At)`: 雲、気体、雨、散乱、総減衰（dB）
