```
G = grid_at_sensor(fname::String, sds_name::String=""; V::Bool=false, kw...)
```

緯度と経度の配列に座標がある、規則的なグリッドではないnetCDFファイルの1つを読み込みます。MODIS L2ファイルはその良い例です。これらのファイルのデータは規則的なグリッドに配置されておらず、グリッドを取得するために補間する必要があります。通常、経度と緯度の配列は$longitude$と$latitude$と呼ばれ、これがデフォルトで探されるものです。しかし、CFに準拠していると主張するファイルも存在しますが、別の名前を使用しています。この場合、`xarray`および`yarray`のキーワード引数を使用して変数名を渡します。例えば：`xarray="XLONG"`, `yarray="XLAT"` 読み込む/補間する配列の名前を渡すために、`sds_name`引数を使用します。

  * `band`: より単純なケースでは、補間される変数は2D配列に配置されていますが、3D配列に格納されている可能性もあります。その場合は、キーワード'band'を使用してバンドを選択します（例：'band=2'）。バンドは1から番号が付けられます。
  * `region` | `limits`, `inc` | `increment` | `spacing`および`search_radius`: 補間はこれまで$nearneighbor$を使用して行われています。地域（-R）と増分（-I）はデータから推定されますが、`region`および`inc`のキーワード引数で設定することもできます。また、オプション`search_radius`を使用して$nearneighbor$の検索半径を設定することもできます。デフォルトでは、`search_radius`は平均増分の2倍に設定されます。
  * `quality`: MODISデータの場合、データの質でフィルタリングするために品質フラグを選択できます。デフォルトでは最高品質（=0）が使用されますが、`quality=val`のキーワード引数で別のものを選択できます。正の'val'値は品質<=品質のデータを選択し、負の'val'値は品質>= abs(val)のデータのみを選択します。これにより、例えば雲のカバレッジのみを抽出することができます。
  * `t_srs`または`target_proj`: 一部の極地グリッドは、地理座標の$longitude$、$latitude$（または単に$lon$、$lat$）配列を持っています。これには（不明瞭な）理由があるはずですが、実際の結果は混乱を招きます。なぜなら、座標間隔が非常に変動するため、適切な推測ができないからです。このような場合、グリッド化の前にデータを再投影することが有用です。その目的のために、`t_srs`または`target_proj`オプションを使用して、グリッド化の前に座標変換を行うようプログラムに指示します。`t_srs`は、目的の投影システムを持つproj4文字列である必要があります。
  * `nodata`: 時々、データセットはNaN以外の値を使用してノーデータを表現しますが、netCDF属性でそれを指定していません（*例* NSIDC製品）。このオプションを使用すると、これを修正できます（*すなわち* `nodata=-9999`）。NSIDC製品には自動的に設定されることに注意してください。
  * `nointerp`: 近隣補間を行わないことを意味しますが、`region`が設定されている必要があります。
  * `NSIDC_N`および`NSIDC_S`: See Ice NSIDC https://nsidc.org/data/polar-stereo/ps*grids.html グリッドを読み込むために、`s*srs`、`region`、`nointerp`、`nodata`を適切に設定します。
  * `dataset`または`xyz`: グリッドを計算する代わりに（GMTgridタイプとして返される）ユーザーがx,y,zデータ自体を望む場合は、キーワード`dataset`または`xyz`を使用し、出力はGMTdatasetになります（すなわち`dataset=true`を使用）。

利用可能な配列のリストのみを照会するには、`list=true`を使用するか、完全なファイル情報を取得するには`gdalinfo=true`を使用します。

```
Examples:

G = grid_at_sensor("AQUA_MODIS.20020717T135006.L2.SST.nc", "sst", V=true);

G = grid_at_sensor("TXx-narr-annual-timavg.nc", "T2MAX", xarray="XLONG", yarray="XLAT", V=true);

G = grid_at_sensor("RDEFT4_20101021.nc", "sea_ice_thickness", NSIDC_N=true);
```
