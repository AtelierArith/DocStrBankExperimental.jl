```
TiltRegion(
    ID   :: AbstractString,
    pID  :: AbstractString,
    name :: AbstractString,
    X    :: Real,
    Y    :: Real,
    ΔX   :: Real,
    ΔY   :: Real,
    θ    :: Real;
    save :: Bool = false,
    path :: AbstractString = pwd(),
    verbose :: Bool = false,
    ST = String,
    FT = Float64
) -> geo :: TiltRegion{ST,FT}
```

傾斜した長方形のGeoRegionを作成します。

# 引数

  * `ID` : GeoRegionを識別するために使用されるキーワードID。           IDがすでに使用されている場合、エラーが発生します。
  * `pID` : 情報を抽出できる親GeoRegionのID。
  * `name` : GeoRegionの名前（メタ情報、ログに使用できます）。
  * `X`  : 地域中心の経度座標。
  * `Y`  : 地域中心の緯度座標。
  * `ΔX` : 経度座標の半幅（傾斜前）。
  * `ΔY` : 緯度座標の半幅（傾斜前）。
  * `θ`  : 長方形地域の傾斜（**度**単位）。

# キーワード引数

  * `save` : `true`の場合、指定された`path`のカスタムGeoRegionsのリストにGeoRegionを保存します。
  * `path` : カスタムGeoRegionsのリストが取得されるパス。          デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `verbose` : 監視を容易にするための詳細なログ？ デフォルトは`false`です。

# 戻り値

  * `geo` : 傾斜した長方形のGeoRegion。
