```julia
print_cpp_header(io, H; namespace_name)

```

出力C++ヘッダーは、圧縮スパース列（CSC）形式でスパースバイナリ（ゼロと1のみを含む）行列Hを格納します。

Juliaの1ベースのインデックスからC++の0ベースのインデックスへの変換に注意してください（CSC形式内でも）！
