```
screenshot_to_GeoData(filename::String, Corner_LowerLeft, Corner_UpperRight; Corner_LowerRight=nothing, Corner_UpperLeft=nothing, Cartesian=false, UTM=false, UTMzone, isnorth=true, fieldname::Symbol=:colors)
```

ジオリファレンスされた画像のスクリーンショットを取得します。これは、指定された深さまたはプロファイルに沿って、`lat/lon`、`x,y`（`Cartesian=true`の場合）またはUTM座標（`UTM=true`の場合）で、`GeoData`、`CartData`、または`UTMData`構造体に変換され、Paraviewに保存できます。

画像の左下および右上の座標は、`(lon,lat,depth)`または`(UTM_ew, UTM_ns, depth)`のタプルで指定する必要があります。ここで、`depth`は地球内部で負（km単位）です。

右下および左上のコーナーはオプションで指定できます（非直交画像を考慮するため）。指定されていない場合、画像は直交と見なされ、他の2つのコーナーから計算されます。

*注意*: データが`UTM`座標の場合、`UTMzone`と北半球にいるかどうか（`isnorth`）も提供する必要があります。
