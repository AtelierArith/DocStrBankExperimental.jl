```
base64decode(string)
```

base64でエンコードされた`string`をデコードし、デコードされたバイトの`Vector{UInt8}`を返します。

関連項目として[`base64encode`](@ref)があります。

# 例

```jldoctest
julia> b = base64decode("SGVsbG8h")
6-element Vector{UInt8}:
 0x48
 0x65
 0x6c
 0x6c
 0x6f
 0x21

julia> String(b)
"Hello!"
```
