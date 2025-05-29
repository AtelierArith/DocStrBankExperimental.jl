```
write_IOexamples(filepath::AbstractString, examples::Vector{IOExample})
```

IO例をディスクに書き込むために、それらをHDF5を使用してファイルにシリアル化し、`.xio`ファイルの拡張子を確認して追加します。
