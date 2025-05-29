```
display_bibliography(bibtexpath::String, citations) ::HypertextLiteral.Result
```

Returns all cited references from a reference BibTex file at `bibtexpath` and `citations`. It can also be bound to a variable to be used with [`show_abstract`](@ref)

See also [`@cite_str`](@ref), [`References`](@ref)
