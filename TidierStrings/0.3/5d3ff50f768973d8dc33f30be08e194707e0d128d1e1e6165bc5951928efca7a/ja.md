```
str_conv(string::Union{String,Vector{UInt8}}, encoding::String)
```

文字列を異なるエンコーディングに変換します。

引数

  * `string`: 入力文字列。
  * `encoding`: 使用するエンコーディングを指定する文字列。

返り値 変換された文字列。

例

```jldoctest
julia> str_conv("Hello, World!", "UTF-8")
"Hello, World!"

julia> str_conv("Hello, World!", "ASCII")
"Hello, World!"

julia> str_conv("Héllo, Wörld!", "ISO-8859-1")
"Héllo, Wörld!"

julia> str_conv([0x48, 0x65, 0x6C, 0x6C, 0x6F, 0x2C, 0x20, 0x77, 0x6F, 0x72, 0x6C, 0x64, 0x21], "UTF-8")
"Hello, world!"
```
