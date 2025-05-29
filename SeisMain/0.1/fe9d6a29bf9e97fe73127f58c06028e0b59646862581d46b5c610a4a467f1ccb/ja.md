```
SeisRead(filename;<keyword arguments>)
```

指定されたファイル名からseis形式の地震データを読み込みます。この形式は3つの要素で構成されています：

  * 幾何情報を含むテキストファイル（データの範囲）
  * データを含むバイナリファイル（@data@）
  * ヘッダーを含むバイナリファイル（@headers@）

# キーワード引数

  * `group="all"` : オプションはall、some、またはgather
  * `key=["imx","imy"]`
  * `itrace=1` : 関数が読み始めるトレースの番号
  * `ntrace=10000` : 読み取るトレースの総数

# 出力

  * d: 2次元配列としてのデータ
  * h: 1次元配列としてのヘッダー
  * extent: データの範囲（この情報を確認するには *fieldnames(Extent)* を試してください）

# 例

```julia
d,h,ext = SeisRead(filename)
```

*クレジット: AS, 2015*
