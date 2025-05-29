```
mutable struct Observation
```

超新星の単一の観測で、時間、フラックス、マグニチュード、フィルター情報を含みます。

# フィールド

  * `name::String`: 超新星の名前
  * `time::typeof(1.0u"d")`: 観測の時間（MJD）
  * `flux::typeof(1.0u"Jy")`: 観測のフラックス（ジャンスキー）
  * `flux_err::typeof(1.0u"Jy")`: 観測のフラックス誤差（ジャンスキー）
  * `mag::typeof(1.0u"AB_mag")`: 観測のマグニチュード（ABマグニチュード）
  * `mag_err::typeof(1.0u"AB_mag")`: 観測のマグニチュード誤差（ABマグニチュード）
  * `absmag::typeof(1.0u"AB_mag")`: 観測の絶対マグニチュード（ABマグニチュード）
  * `absmag_err::typeof(1.0u"AB_mag")`: 観測の絶対マグニチュード誤差（ABマグニチュード）
  * `filter::Filter`: 超新星を観測するために使用された[`Filter`](@ref)
  * `is_upperlimit::Bool`: 観測が上限値であるかどうか
