```
gdaltranslate(indata, options=String[]; dest="/vsimem/tmp", kwargs...)
```

異なるフォーマット間でラスターデータを変換します。

GDALの'gdal_translate'ツールによって提供される操作。具体的には、サブリージョンの抽出とリサンプリングです。`kwargs`オプションは、GMT領域（-R）、インクリメント（-I）、ターゲットSRS（-J）を受け入れます。キーワードのいずれかである`outgrid`、`outfile`、または`save` = outputnameオプションを使用して、この関数が'result'を'outputname'で指定されたファイルに保存するようにします。ファイル形式は'outputname'のファイル拡張子から選択されます。出力ファイル名が提供されていない場合、入力タイプに応じてGMTオブジェクト（グリッドまたは画像）を返します。GDALデータセットの返却を強制するには、オプション`gdataset=true`を使用します。

### 引数

  * `indata`: 入力データ。ファイル名、GMTgridまたはGMTimageオブジェクト、またはGDALデータセットである可能性があります。
  * `options`: オプションのリスト。受け入れられるオプションはgdal_translateユーティリティのものです。このリストは、文字列のベクターの形、または単一の文字列に結合された形で提供できます。

### Kwargs

  * `meta=metadata`、ここで`metadata`は各要素の形式が"NAME=...."の文字列ベクターです。このデータはGDALによってメタデータとして認識されます。

`kwargs`には、GMT領域（-R）、proj（-J）、inc（-I）、および`save=fname`オプションも含まれる場合があります。

### 戻り値

GMTグリッドまたは画像、またはGDALデータセット（またはファイルがディスクに書き込まれた場合は何も返しません）。
