```julia
save_to_bincscjson(destination_file_path, mat; varargs...)

```

ファイルで使用するためのヘルパーメソッド。メインインターフェースについては `print_bincscjson` を参照してください。

圧縮スパースカラム（CSC）ストレージを定義する2つの配列 `colptr` と `rowval` をjsonファイルに書き込みます。スパース行列が1と0のみを含む場合を除き、エラーが発生します。CSC形式の3番目の配列、すなわち非ゼロエントリは必要ありません。行列は1と0のみを含むと仮定されているためです。
