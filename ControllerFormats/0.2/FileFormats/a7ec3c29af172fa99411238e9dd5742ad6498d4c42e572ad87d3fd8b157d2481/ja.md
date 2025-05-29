```
read_MAT(filename::String; act_key::String)
```

MATLABの[`MAT`](https://www.mathworks.com/help/matlab/import_export/load-parts-of-variables-from-mat-files.html)形式で保存されたニューラルネットワークを読み込みます。この関数は[`MAT.jl`ライブラリ](https://github.com/JuliaIO/MAT.jl)をロードする必要があります。

### 入力

  * `filename` – `MAT`ファイルの名前
  * `act_key`  – 活性化関数に使用されるキー
  * `net_key`  – （オプション; デフォルト: `nothing`）ニューラルネットワークに使用されるキー

### 出力

[`FeedforwardNetwork`](@ref)。

### 注意事項

`MATLAB`ファイルは辞書をエンコードしています。`net_key`が指定されている場合、辞書はこのキーの下に別の辞書を含みます。そうでない場合、外側の辞書は直接以下を含みます：

  * 重み行列のベクトル（名前は`"W"`）
  * バイアスベクトルのベクトル（名前は`"b"`）
  * 活性化関数の文字列のベクトル（`act_key`を介して渡された名前の下）
