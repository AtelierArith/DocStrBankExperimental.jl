```
LAS(io)
LAS(filename)
LAS(url; cache = true)
```

ファイル、URL、または任意の `IO` 入力からLAS/LAZデータを読み込みます（圧縮されたLAZデータには対応していません）。詳細については、[`Base.read(input, LAS)`](@ref Base.read(::IO, ::Type{LAS}))を参照してください。
