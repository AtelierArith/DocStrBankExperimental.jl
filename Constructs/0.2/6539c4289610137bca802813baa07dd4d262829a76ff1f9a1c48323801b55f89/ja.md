```
Padded([T|subcon = Nothing], n) -> Construct{T}
```

`subcon`から`n`バイトのパディングデータを作成します。

# 引数

  * `subcon::Construct{T}`: パディングされる構造体。
  * `n::Integer`: パディング後のサイズ（バイト単位）。

# 例

```jldoctest
julia> deserialize(Padded(Int8, 2), b"\x01\xfc")
1

julia> serialize(Padded(Int8, 2), Int8(1))
2-element Vector{UInt8}:
 0x01
 0x00
```
