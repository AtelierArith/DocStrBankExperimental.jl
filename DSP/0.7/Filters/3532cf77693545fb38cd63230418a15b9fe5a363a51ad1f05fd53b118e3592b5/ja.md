```
FIRFilter(h[, ratio])
```

フィルタタップのベクトル `h` から状態を持つ FIRFilter オブジェクトを構築します。`ratio` はオプションの有理整数で、入力から出力サンプルレートの関係を指定します（例：録音された音声を 48 KHz から 44.1 KHz に変換するための `147//160`）。
