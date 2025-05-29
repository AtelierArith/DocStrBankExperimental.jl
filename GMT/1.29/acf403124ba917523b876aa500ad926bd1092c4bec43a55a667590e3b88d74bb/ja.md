```
O = gd2gmt(dataset; band=0, bands=[], sds=0, pad=0)
```

GDALラスターデータセットを、タイプがInt16またはFloatの場合はGMTgridに、そうでない場合はGMTimageタイプに変換します。`band`を使用してデータセットの単一バンドを選択します。データセットに複数のバンドが含まれていることがわかっている場合は、希望するバンドのベクターを持つキーワード引数`bands`を使用します。デフォルトでは、画像またはグリッドオブジェクトのすべてのバンドを読み取ります。

DATASETが文字列の場合、ファイル名またはサブデータセットの名前を含むことがあります。前者の場合、キーワード引数`sds`を使用して数値的にサブデータセットを選択できます。あるいは、完全な`sds`名を提供してください。スケールファクターを持つ`sds`を持つファイル（例：MODISデータ）の場合、そのスケールは自動的に適用されます。

### 例:

G = gd2gmt("AQUA_MODIS.20210228.L3m.DAY.NSST.sst.4km.NRT.nc", sds=1);

または

G = gd2gmt("SUBDATASET*1*NAME=NETCDF:AQUA_MODIS.20210228.L3m.DAY.NSST.sst.4km.NRT.nc:sst");

または

G = gd2gmt("NETCDF:AQUA_MODIS.20210228.L3m.DAY.NSST.sst.4km.NRT.nc:sst");
