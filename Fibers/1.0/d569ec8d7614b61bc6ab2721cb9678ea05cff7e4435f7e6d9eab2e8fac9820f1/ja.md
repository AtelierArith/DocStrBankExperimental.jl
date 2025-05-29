```
xfm_read(matfile::String, inref::MRI, outref::MRI, T::DataType=Float32)
```

.matファイルから変換を読み込み、`Xform`構造体を返します

変換の入力および出力空間の参照ボリュームも、`MRI`構造体として指定する必要があります。
