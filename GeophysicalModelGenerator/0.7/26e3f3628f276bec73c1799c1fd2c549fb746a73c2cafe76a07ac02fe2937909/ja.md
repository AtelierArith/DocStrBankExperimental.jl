```
Datasets = load_dataset_file(file_datasets::String)
```

これは、データセットのリストを含むCSVテキストファイルを読み込みます。ファイルは以下の形式であることが期待されます：

  * `Name`,`Location`,`Type`, `[Active]`
  * AlpArray,./Seismicity/ALPARRAY/AlpArraySeis.jld2,Point, true
  * Plomerova2022,https://seafile.rlp.net/f/abccb8d3302b4ef5af17/?dl=1,Volume

ファイルの最初の行はスキップされることに注意してください。

ここで、変数の意味は次のとおりです：

  * `Name`: 読み込むデータセットの名前
  * `Location`: ローカルマシン上のファイルの場所（ディレクトリとファイル名）または、ウェブからファイルをダウンロードできるURL。URLは「http」で始まることが期待されます。
  * `Type`: データセットのタイプ（Volume, Surface, Point, Screenshot）
  * `Active`: このファイルを読み込みたいかどうか？デフォルトは`true`のオプションパラメータです。
