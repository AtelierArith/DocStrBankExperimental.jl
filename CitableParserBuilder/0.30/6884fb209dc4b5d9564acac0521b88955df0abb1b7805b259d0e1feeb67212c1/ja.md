`Cite2Urn` から `AbbreviatedUrn` 文字列を構築します。

```julia
abbreviate(urn)

```

例:

```julia-repl
julia> abbreviate(Cite2Urn("urn:cite2:kanones:lsj.v1:n123"))
"lsj.n123"
```

例: `Cite2Urn` を省略し、省略された文字列値から `LexemeUrn` を形成するパイプライン。

```julia-repl
julia> Cite2Urn("urn:cite2:kanones:lsj.v1:n123") |> abbreviate |> LexemeUrn
LexemeUrn("lsj", "n123")
```
