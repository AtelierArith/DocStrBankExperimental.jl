```
dither(indata; n_colors=256, save="", gdataset=false)
```

24ビットRGB画像を8ビットパレットに変換します。

  * `save=fname`オプションを使用して、結果をGeoTiffファイル`fname`にディスクに保存します。`fname`に拡張子がない場合は、`.tif`が追加されます。代わりに、`.png`または`.nc`の拡張子を持つファイル名を指定して、これらの形式のいずれかでファイルを保存します。
  * `gdataset=true`: GDALデータセットを返します。デフォルトはGMTimageオブジェクトを返します。
  * `n_colors`: 生成されるカラーテーブルの色数を選択します。デフォルトは256です。
