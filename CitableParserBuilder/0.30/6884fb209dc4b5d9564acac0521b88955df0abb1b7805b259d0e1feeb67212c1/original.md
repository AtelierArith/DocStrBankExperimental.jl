Constructs an `AbbreviatedUrn` string from a `Cite2Urn`.

```julia
abbreviate(urn)

```

Example:

```julia-repl
julia> abbreviate(Cite2Urn("urn:cite2:kanones:lsj.v1:n123"))
"lsj.n123"
```

Example: a pipeline abbreviating a `Cite2Urn` and forming a `LexemeUrn` from the abbreviated string value.

```julia-repl
julia> Cite2Urn("urn:cite2:kanones:lsj.v1:n123") |> abbreviate |> LexemeUrn
LexemeUrn("lsj", "n123")
```
