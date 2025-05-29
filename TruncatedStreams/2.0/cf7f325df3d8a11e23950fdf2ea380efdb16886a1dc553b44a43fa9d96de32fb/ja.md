```
FixedLengthSource(io, length) <: TruncatedSource
```

`io` から `length` バイトまで読み取る切り詰められたソースです。

```jldoctest fixedlengthio_1
julia> io = IOBuffer(collect(0x00:0xff));

julia> fio = FixedLengthSource(io, 10);

julia> read(fio)
10-element Vector{UInt8}:
 0x00
 0x01
 0x02
 0x03
 0x04
 0x05
 0x06
 0x07
 0x08
 0x09

julia> eof(fio)
true
```

`FixedLengthSource` オブジェクトからの読み取りが基盤となる IO ストリームの `length` バイトを超えると、EOF が信号され、`EOFError` がスローされる可能性があります。

```jldoctest fixedlengthio_1
julia> read(fio, Int)
ERROR: EOFError: read end of file
[...]
```

シークはストリームが切り詰められる長さには影響しませんが、読み取れるバイト数には影響を与える可能性があります。

```jldoctest fixedlengthio_1
julia> seek(fio, 8); read(fio)
2-element Vector{UInt8}:
 0x08
 0x09
```
