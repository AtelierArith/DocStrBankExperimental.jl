```
convert_dgm_2d(path_read::String, path_write::String; excerpt = 1)
```

[DGM](https://www.opengeodata.nrw.de/produkte/geobasis/hm/dgm1_xyz/dgm1_xyz/) データファイルを二次元の読み取り可能なファイルに変換する関数です。

入力:

  * `path_read`: 変換するDGMデータのパスの文字列
  * `path_write`: 新しいファイルを保存するパスの文字列。（ファイル名も含める必要があります）
  * `excerpt`: 抽出されるデータのストライドを指定するオプションの整数。例えば、excerptが10に設定されている場合、10番目の`x`および`y`値とそれに対応する`z`値のみが考慮されます。デフォルト値は1で、すべての値が取得されます。
