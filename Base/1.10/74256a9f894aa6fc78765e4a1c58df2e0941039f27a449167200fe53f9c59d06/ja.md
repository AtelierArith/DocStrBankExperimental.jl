```
PipeBuffer(data::Vector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

[`IOBuffer`](@ref) は読み取りを許可し、追加によって書き込みを行うバッファです。シークや切り詰めはサポートされていません。利用可能なコンストラクタについては [`IOBuffer`](@ref) を参照してください。`data` が指定されている場合、データベクター上で操作するための `PipeBuffer` を作成し、基盤となる `Array` が成長できないサイズをオプションで指定します。
