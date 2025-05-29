```
trcs = readframetrcs(io::CSeis, idx...; regularize=true)
```

`io`からフレーム`idx...`のトレースを読み込みます。`idx...`は整数または`CartesianIndex`のいずれかです。

`regularize`という名前付き引数は、圧縮方法が`LeftJustifyCompressor`の場合にのみ適用されます。trueに設定すると、トレースは正しいコンテキスト位置に正規化されます。それ以外の場合、トレースは左揃えのままです。後で`regularize!`メソッドを使用することもできます。
