```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

I/O ストリームまたはファイルから、指定された区切り文字までの文字列を読み取ります。区切り文字は `UInt8`、`AbstractChar`、文字列、またはベクターであることができます。キーワード引数 `keep` は、区切り文字が結果に含まれるかどうかを制御します。テキストは UTF-8 でエンコードされていると仮定されます。

# 例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
