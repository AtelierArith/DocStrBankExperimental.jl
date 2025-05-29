```
extensions(fp::AbstractPath) -> AbstractString
```

ファイル名からすべての拡張子を抽出します。拡張子がない場合は、空の文字列を返します。

# 例

```jldoctest
julia> extensions(p"~/repos/FilePathsBase.jl/src/FilePathsBase.jl.bak")
2-element Array{SubString{String},1}:
 "jl"
 "bak"
```
