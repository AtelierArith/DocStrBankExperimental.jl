```julia
GEOSFP(domain, domaininfo; name, stream)

```

GEOS-Chem classicで使用するためにアーカイブされたGEOS-FPデータのデータローダーです。

ドメインオプション（2022-01-30現在）：

  * 4x5
  * 0.125x0.15625_AS
  * 0.125x0.15625_EU
  * 0.125x0.15625_NA
  * 0.25x0.3125
  * 0.25x0.3125_AF
  * 0.25x0.3125_AS
  * 0.25x0.3125_CH
  * 0.25x0.3125_EU
  * 0.25x0.3125_ME
  * 0.25x0.3125_NA
  * 0.25x0.3125_OC
  * 0.25x0.3125_RU
  * 0.25x0.3125_SA
  * 0.5x0.625
  * 0.5x0.625_AS
  * 0.5x0.625_CH
  * 0.5x0.625_EU
  * 0.5x0.625_NA
  * 2x2.5
  * 4x5
  * C180
  * C720
  * NATIVE
  * c720

このデータセットのネイティブデータ型はFloat32です。

`stream`は、データを必要に応じてストリーミングするか、一度にすべて読み込むかを指定します。

現在のデータドメインオプションについてはhttp://geoschemdata.wustl.edu/ExtData/を参照してください。
