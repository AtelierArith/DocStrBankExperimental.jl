```
makeDCWs(fname; float=false, name_cdl="xxxx.cdl", name_nc="", compress=true,
         attrib="", fix_RU::Bool=false, deltmp=true)
```

OGRファイル`fname`の内容をGMT DCW形式の構造を持つNetCDF CDLまたはNCファイルに変換します。これまでのところ、管理レベル0のポリゴン（国境）のみがサポートされています。

### パラメータ

  * `fname`: 変換するファイルの名前。ポリゴンとISO 3166-1 Alpha-3またはAlpha-2のコードを含むメタデータを持つOGR読み取り可能なファイルである必要があります。注意: 変換されるファイルがOpenDataSoftの「world-administrative-boundaries」である場合（下記の完全なリンクを参照）、南極のポリゴンが欠けています。これを取得するためのトリックは、Natural Earthファイルから南極のポリゴンを抽出することです。具体的には、「ne*10m*admin*0*countries.shp.zip」という名前のファイルが変換されるファイルと同じディレクトリに存在する場合、それを使用して欠けている南極のポリゴンを抽出します。

### キーワード

  * `attrib`: OGRファイル内の国コードを含む属性フィールドの名前。ISO 3166-1 Alpha-3またはAlpha-2コードのいずれかである必要があります。便利のために、'Natural Earth' https://www.naturalearthdata.com/downloads/10m-cultural-vectors/ ファイルのデフォルト（`attrib="ADM0_A3"`）、'World Administrative Boundaries' https://public.opendatasoft.com/explore/dataset/world-administrative-boundaries/export/ （`attrib="iso3"`）、および'Open Street Maps'（`attrib="iso2"`）を提供します。他の製品については、最初に`gmtread`でファイルを読み込み、属性を確認して国コードを保持する属性名を見つける必要があります。例えば: $o = gmtread("the_file"); info(o[1].attrib)$
  * `float`: trueの場合、座標を32ビット浮動小数点で保存します。デフォルトは、座標をUInt16変数に収まるようにスケーリングするスキームを使用します。GMTはUInt16およびFloat32ファイルの両方を読み取る方法を知っています。
  * `name_cdl`: CDLファイルの名前（デフォルト: "xxxx.cdl"）。このファイルは`deltmp` = trueの場合に削除されます。
  * `name_nc`: 最終的なnetCDFファイルの名前。警告: この操作が機能するためには、実行可能ファイル`ncgen`がパスに存在することが必須です。
  * `compress`: trueの場合、ncファイルをレベル9で圧縮します（デフォルト: true）。`name_nc`が空でない場合にのみ使用され、実行可能ファイル`nccopy`がパスに存在する必要があります。
  * `fix_RU`: ロシアのポリゴンはしばしば日付変更線で分割されます。これが真であり、このオプションが`true`の場合、シベリアの2つの部分を1つの大きなロシアのポリゴンに統合しようとします。デフォルトは`false`で、この操作が失敗する可能性が低くないためです。この試みが失敗した場合は`false`に設定し、分割されたポリゴンで妥協します。
  * `deltmp`: 一時ファイルを削除します（デフォルト: true）。`name_nc`が空でない場合にのみ使用されます。

### 例

```julia
# ne_10m_admin_0_countries_iso.shp.zipファイルからUint16にスケーリングされたデータを持つxxxx.cdlファイルを作成します
makeDCWs("ne_10m_admin_0_countries_iso.shp.zip")

# その後、コマンドラインでnetCDFファイル"NE10m.nc"を作成するには、次のように実行します:
ncgen -b -k 3 -o NE10m.nc -x xxxx.cdl

# そして、レベル9で圧縮するには
nccopy -k 3 -d 9 -s NE10m.nc NE10m_9.nc

# 単精度でデータが保存された圧縮netCDFファイル"NE10m.nc"を作成するには
makeDCWs("ne_10m_admin_0_countries_iso.shp.zip", name_nc="NE10m_f32.nc", float=true)
```
