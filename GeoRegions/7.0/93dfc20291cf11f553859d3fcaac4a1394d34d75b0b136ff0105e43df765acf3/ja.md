```
readGeoRegions(
    fname :: AbstractString
) -> gvec :: Vector{<:GeoRegion}
```

`fname`で定義されたファイルからGeoRegionの情報を抽出します。

# 引数

  * `fname` : GeoRegion情報を含むファイルの名前 + パスを指定する文字列。

# 戻り値

  * `gvec` : ファイル`fname`内のすべてのGeoRegionを含むベクター。
