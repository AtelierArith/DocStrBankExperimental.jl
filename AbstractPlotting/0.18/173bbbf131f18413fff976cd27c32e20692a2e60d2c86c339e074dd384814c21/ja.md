```
convert_arguments(P, Matrix)::Tuple{ClosedInterval, ClosedInterval, Matrix}
```

`AbstractMatrix`を受け取り、次元`n`と`m`を`ClosedInterval`に変換し、`ClosedInterval`を`n`と`m`に格納し、元の行列をタプルに保存します。

`P`はプロットタイプ（オプション）です。
