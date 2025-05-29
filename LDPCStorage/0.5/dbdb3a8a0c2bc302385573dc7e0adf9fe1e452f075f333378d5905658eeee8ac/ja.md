```julia
save_to_qccscjson(destination_file_path, mat; varargs...)

```

ファイルで使用するためのヘルパーメソッド。メインインターフェースについては `print_qccscjson` を参照してください。

行列の圧縮スパースカラム (CSC) ストレージを定義する3つの配列をファイルに書き込みます。これは準周期的LDPC行列の指数を保存するために使用されます。QC拡張係数を指定する必要があります。
