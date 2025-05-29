```
TypstCommand(::AbstractVector{<:AbstractString})
TypstCommand(::TypstCommand; kwargs...)
```

Typstコンパイラとそのパラメータ。

キーワードパラメータは`Cmd`と同じ意味を持ちます。

!!! info
    この型は`Cmd`インターフェースを実装しています。ただし、インターフェースは文書化されていないため、予期しない動作が発生する可能性があります。


# 例

```jldoctest
julia> help = TypstCommand(["help"])
typst`help`

julia> TypstCommand(help; ignorestatus = true)
typst`help`
```
