Compose SFST representation of an `AbbreviatedUrn`.

```julia
fstsafe(au)

```

Example:

```julia-repl
julia> LexemeUrn("lexicon.lex123") |> fstsafe
"<u>lexicon\.lex123</u>"
```
