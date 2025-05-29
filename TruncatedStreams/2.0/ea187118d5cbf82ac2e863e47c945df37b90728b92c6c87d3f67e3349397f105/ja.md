```
SentinelizedSource(io, sentinel) <: TruncatedSource
```

`sentinel`が見つかるまで`io`を読み取る切り詰められたソースです。

```jldoctest sentinelio_1
julia> io = IOBuffer(repeat(collect(0x00:0x0f), 2));

julia> sio = SentinelizedSource(io, [0x0a, 0x0b]);

julia> read(sio)
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

julia> eof(sio)
true
```

`SentinelizedSource`オブジェクトからの読み取りが、基盤となるIOストリームから`sentinel`に一致するバイトシーケンスの先頭を読み取ることになると、EOFが信号され、`EOFError`がスローされる可能性があります。

```jldoctest sentinelio_1
julia> read(sio, Int)
ERROR: EOFError: read end of file
[...]
```

シークは、ストリームがセンチネルの最初のバイトで終了するかのように機能します。後方シークは、ラップされたストリームがそれを許可する限り常に成功し、前方シークはセンチネルまでしかシークしません。前方シークはラップされたストリームからバイトを消費することに注意してください。

```jldoctest sentinelio_1
julia> seek(sio, 8); read(sio)
2-element Vector{UInt8}:
 0x08
 0x09
```

eofの検出は、`Base.reseteof()`メソッドでリセットできます。これは、読み取ったセンチネルがさらなる検査によって偽であると判断された場合に使用します。

```jldoctest sentinelio_1
julia> Base.reseteof(sio)  # 最後のセンチネルは偽物だったので、EOFをリセットして再度読み取る

julia> read(sio)  # 最初に見つかったセンチネルを返し、次のセンチネルが見つかるまで読み続ける
16-element Vector{UInt8}:
 0x0a
 0x0b
 0x0c
 0x0d
 0x0e
 0x0f
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
```

!!! note
    ラップされたストリームにセンチネルが含まれていない場合、ストリームの終わりまで読み取ると`EOFError`がスローされます。


```jldoctest sentinelio_3
julia> io = IOBuffer(collect(0x00:0x07)); sio = SentinelizedSource(io, [0xff, 0xfe]);

julia> read(sio)
ERROR: EOFError: read end of file
[...]
```
