```
gzi(io::IO)
```

BGZFファイルを表す`IO`のGZIを持つ`Vector{UInt8}`を構築します。GZIファイルには、BGZFファイル内の各ブロックとその解凍ペイロードのオフセットが含まれています。GZIファイルは、BGZFファイル内の解凍データのサイズの約1/4000です。

## 例

```julia
julia open(gzi, "/my/bgzip/file.bgz")
102744-element Array{UInt8,1}:
 0x15
 0x19
 0x00
 0x00
 0x00
[ ... ]
```
