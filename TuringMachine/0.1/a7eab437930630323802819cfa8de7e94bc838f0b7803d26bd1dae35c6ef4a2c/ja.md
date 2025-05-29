```
load_program(file_name)
```

テキストファイルを読み込み、チューリングプログラムを含みます。このプログラムの書き方については、ドキュメントを参照してください。

入力

  * `file_name`::string : シミュレートするチューリングプログラムを含むテキストファイルのパス

出力

  * `program`::Dict{Any,Any} で `m` エントリを持つ: [states,read*cells] のキーと [next*state,write_cell,movement] の値を持つ辞書
