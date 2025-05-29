```
cl = coastlinesproj(proj="?", res="crude", coastlines=nothing)
```

GMTのGSHHGデータベースから海岸線を抽出し、PROJを使用して投影します（GMTの投影機構ではありません）。これにより、純粋なGMTでは利用できない多くのPROJ投影を使用できます。

  * `proj`: 投影を説明するproj4文字列（必須）。
  * `res`: GSHHG海岸線の解像度。利用可能なオプションは：`crude`、`low`、`intermediate`、`high`、および`full`です。
  * `coastlines`: `res`オプションの代わりに、別のソースから（`gmtread`で）以前に読み込まれた海岸線を持つGMTdatasetを渡すことができます。
  * `limits`: 空でない場合、lon*min、lon*maxの2要素の配列でなければならず、360度以上に拡張する海岸線を要求するために使用されます（`worldrectangular`はこれを使用します）。

### 戻り値

解像度`res`で投影された（または投影されていない）世界のGSHHG海岸線を含むGMTdatasetのベクター。

### 例

```
cl = coastlinesproj(proj="+proj=ob_tran +o_proj=moll +o_lon_p=40 +o_lat_p=50 +lon_0=60");
```
