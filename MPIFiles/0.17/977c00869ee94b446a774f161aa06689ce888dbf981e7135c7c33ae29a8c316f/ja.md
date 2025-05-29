```julia
TransferFunction(filename::String; kargs...) -> Any

```

`filename`でデータファイルから`TransferFunction`を作成します。

ファイルは、このパッケージで作成されたh5ファイルか、VNAによって書き込まれたファイルのいずれかです。キーワード引数は`load_tf_fromVNA`に渡されます。
