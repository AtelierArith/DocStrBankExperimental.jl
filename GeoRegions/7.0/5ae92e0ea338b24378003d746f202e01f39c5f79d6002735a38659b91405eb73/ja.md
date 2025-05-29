```
PolyRegion(
    ID   :: AbstractString,
    pID  :: AbstractString,
    name :: AbstractString,
    lon  :: Vector{<:Real},
    lat  :: Vector{<:Real};
    join :: Bool = true,
    save :: Bool = false,
    path :: AbstractString = pwd(),
    verbose :: Bool = false,
    ST = String,
    FT = Float64
) -> geo :: PolyRegion{ST,FT}
```

ポリゴン型のGeoRegionを作成します。

# 引数

  * `ID` : GeoRegionを識別するために使用されるキーワードID。           IDがすでに使用されている場合、エラーが発生します。
  * `pID` : 情報を抽出できる親GeoRegionのID。
  * `name` : GeoRegionの名前（メタ情報、ログに使用できます）。
  * `lon` : 経度ポイントを含むベクター。
  * `lat` : 緯度ポイントを含むベクター。

# キーワード引数

  * `join` : `true`の場合、最初と最後の座標ポイントが一致しない場合、形を閉じるために最初の座標を再度追加します。
  * `save` : `true`の場合、指定された`path`のカスタムGeoRegionsのリストにGeoRegionを保存します。
  * `path` : カスタムGeoRegionsのリストが取得されるパス。          デフォルトはユーザーのホームディレクトリ`homedir()`です。
  * `verbose` : `true`の場合、監視を容易にするための詳細なログ。デフォルトは`false`です。

# 戻り値

  * `geo` : ポリゴン型のGeoRegion。
