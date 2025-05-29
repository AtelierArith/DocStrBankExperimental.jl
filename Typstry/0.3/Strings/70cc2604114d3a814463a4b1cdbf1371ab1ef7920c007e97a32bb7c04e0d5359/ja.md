```
TypstString <: AbstractString
TypstString(::Any; context...)
```

値をTypst形式の文字列としてフォーマットします。

オプションのJulia設定とTypstパラメータは、[`show(::IO, ::MIME"text/typst", ::Typst)`](@ref)に`IOContext`で渡されます。サポートされている型のリストについては、[`show_typst`](@ref)を参照してください。

!!! info
    この型は`String`インターフェースを実装しています。ただし、インターフェースは文書化されていないため、予期しない動作が発生する可能性があります。


# 例

```jldoctest
julia> TypstString(1)
typst"$1$"

julia> TypstString(1 + 2im; mode = math)
typst"(1 + 2i)"
```
