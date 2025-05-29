```
RectRegion(
    ID    :: AbstractString,
    pID   :: AbstractString,
    name  :: AbstractString,
    bound :: Vector{<:Real};
    save :: Bool = false,
    path :: AbstractString = pwd(),
    verbose :: Bool = false,
    ST = String,
    FT = Float64
) -> geo :: RectRegion{ST,FT}
```

直線的なGeoRegionを作成します。

# 引数

  * `ID` : GeoRegionを識別するために使用されるキーワードID。           IDがすでに使用されている場合、エラーが発生します。
  * `pID` : 情報を抽出できる親GeoRegionのID。
  * `name` : GeoRegionの名前（メタ情報、ログに使用できます）。
  * `bound` : 地域を定義する[N,S,E,W]座標。

# キーワード引数

  * `save` : `true`の場合、指定された`path`のカスタムGeoRegionsのリストにGeoRegionを保存します。
  * `path` : カスタムGeoRegionsのリストが取得されるパス。          デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `verbose` : 監視を容易にするための詳細なログ？ デフォルトは`false`です。

# 戻り値

  * `geo` : 直線的なGeoRegion。
