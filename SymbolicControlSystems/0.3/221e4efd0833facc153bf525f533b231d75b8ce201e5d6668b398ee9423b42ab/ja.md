```
print_c_array(io, sys::Vector{<:AbstractStateSpace}, t::AbstractVector, name = "sys"; cse = false, s = "", en = "", struct_name::Union{Nothing, String} = nothing, struct_type = nothing)
```

補間線形システムのためのCコードを書いてください。補間ベクトル`t`は補間点を定義し、このベクトルは線形システムのベクトル`sys`と同じ長さであることが期待されます。

  * `s, en`: Cコード内の変数名の先頭と末尾に追加される文字列です。
  * `struct_name`: 提供される場合、補間行列はこの名前の構造体内に配置されます。
  * `struct_type`: 構造体名が使用される場合、構造体のC型も提供してください。
