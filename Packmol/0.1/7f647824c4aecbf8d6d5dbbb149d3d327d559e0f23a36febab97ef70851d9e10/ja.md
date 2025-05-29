```
run_packmol()
run_packmol(input_file::String)
```

入力ファイル `input_file` を使用して packmol 実行可能ファイルを実行します。これは、事前にコンパイルされたバイナリである古典的な `http://m3g.iqm.unicamp.br/packmol` プログラムを実行します。入力ファイルは、packmol 入力ファイルと同じ構文のテキストファイルです。

入力ファイルが提供されていない場合、入力ファイルを選択するためのファイルエクスプローラーが開きます。

ファイルエクスプローラーを無効にするには、環境変数 `PACKMOL_GUI="false"` を設定します。
