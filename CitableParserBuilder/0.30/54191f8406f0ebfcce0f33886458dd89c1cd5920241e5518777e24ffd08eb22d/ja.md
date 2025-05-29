`AbbreviatedUrn`のSFST表現を作成します。

```julia
fstsafe(au)

```

例:

```julia-repl
julia> LexemeUrn("lexicon.lex123") |> fstsafe
"<u>lexicon\.lex123</u>"
```
