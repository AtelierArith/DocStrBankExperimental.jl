```
AuxTag(::Union{String, SubString{String}})
AuxTag(::Char, ::Char)
AuxTag(::UInt8, ::UInt8)
```

`Auxiliary`のキーの型。この型は軽量で、キーが適切な形式であることを検証します。`Auxiliary`は文字列をキーとして使用することもでき、これらは`AuxTag`に変換されますが、これにより文字列の不必要な割り当てが発生する可能性があります。

# 例

```jldoctest
julia> AuxTag("AC")
AuxTag("AC")

julia> AuxTag('k', 'w')
AuxTag("kw")

julia> AuxTag("1C") # 無効なタグ
ERROR: Invalid AuxTag. Tags must conform to r"^[A-Za-z][A-Za-z0-9]$".
[...]
```
