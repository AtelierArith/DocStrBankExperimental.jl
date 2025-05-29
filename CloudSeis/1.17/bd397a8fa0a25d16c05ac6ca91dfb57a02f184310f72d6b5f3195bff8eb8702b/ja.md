```
readframehdrs!(io::CSeis, trcs, idx...; regularize=true)
```

`io`からフレーム`idx...`の`hdrs::Matrix`にヘッダーを読み込みます。`idx...`は整数または`CartesianIndex`のいずれかです。

`regularize`という名前の引数は、圧縮方法が`LeftJustifyCompressor`の場合にのみ適用されます。trueに設定すると、トレースは正しいコンテキスト位置に正規化されます。それ以外の場合、左寄せのままになります。後で`regularize!`メソッドを使用することもできます。
