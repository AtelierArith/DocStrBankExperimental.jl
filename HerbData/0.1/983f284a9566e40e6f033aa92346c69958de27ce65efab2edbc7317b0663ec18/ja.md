```
write_IOPexamples(filepath::AbstractString, examples::Vector{Tuple{IOExample, Any}})
```

IO例と対応するプログラムをディスクに書き込み、HDF5を使用してファイルにシリアライズし、`.xiop`をチェックして追加します。
