```
save_data(filepath::String, data_matrix::AbstractMatrix; 
          header_lines::Vector{String}=String[], 
          delimiter::Char='\t', 
          print_confirmation::Bool=true)
```

データ行列を区切り付きテキストファイル（.dat形式）に保存します。`data_matrix`の各列はファイル内の列として書き込まれます。

# 引数

  * `filepath::String`: データを保存するファイルの完全なパスと名前（例："resultados/datos_simulacion.dat"）。
  * `data_matrix::AbstractMatrix`: 保存するデータの行列。データは列に整理されていることが期待されます。

# キーワード

  * `header_lines::Vector{String}=String[]`: 文字列のベクター。各文字列はファイルの先頭に"# "を付けてヘッダー行として書き込まれます。デフォルトでは、ヘッダーは書き込まれません。
  * `delimiter::Char='\t'`: 列の間に使用する区切り文字。デフォルトはタブ（`'\t'`）です。スペース（`' '`）、カンマ（`,`）など他の文字を使用することもできます。
  * `print_confirmation::Bool=true`: `true`の場合、ファイルを保存した後に確認メッセージを印刷します。

# 例

```julia
x = collect(1.0:0.1:10.0)
y1 = sin.(x)
y2 = cos.(x)
# x, y1, y2をタブで区切られた3つの列として保存
save_data("ejemplo.dat", [x y1 y2], 
          header_lines=["Columna 1: x", "Columna 2: sin(x)", "Columna 3: cos(x)"],
          delimiter='\t')

# ヘッダーなしでスペースを区切り文字として保存
z = x.^2
save_data("otro_ejemplo.dat", [x z], delimiter=' ')
```

# 注意事項

  * この関数は`DelimitedFiles.writedlm`を使用します。
  * `filepath`で指定されたファイルがすでに存在する場合、上書きされます。
