```
addtags[!](siteinds, commoninds, M1::MPO, M2::MPS, args...; kwargs...)
addtags[!](siteinds, commoninds, M1::MPO, M2::MPO, args...; kwargs...)
```

`M1`と`M2`で共有されるサイトインデックスにaddtagsを適用します。

新しいMPS/MPOを返します。MPS/MPOのITensorは、元のITensorのストレージのビューになります。
