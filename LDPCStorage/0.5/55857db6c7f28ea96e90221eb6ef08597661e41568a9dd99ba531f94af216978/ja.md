```julia
print_cpp_header_QC(io, H; expansion_factor, namespace_name)

```

出力C++ヘッダーは、圧縮スパース列（CSC）形式でLDPC行列の準周期指数を格納します。これは、`colptr`、`row_idx`、および`values`と呼ばれる3つの配列を意味します。拡張係数も指定する必要があります（これは単にヘッダー内の変数として格納されます）。

Juliaの1ベースのインデックスからC++の0ベースのインデックスへの変換に注意してください（CSC形式内でも同様です）!
