```
extension(fp::AbstractPath) -> AbstractString
```

ファイル名から最後の拡張子を抽出します。拡張子がない場合は、空の文字列を返します。

# 例

```jldoctest
julia> extension(p"~/repos/FilePathsBase.jl/src/FilePathsBase.jl")
"jl"
```
