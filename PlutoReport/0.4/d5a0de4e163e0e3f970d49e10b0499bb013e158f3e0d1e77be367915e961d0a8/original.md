```
style_citations(citations, bibtexpath::String; css::Union{CiteCSS, HypertextLiteral.Result}=Superscript, content::Union{CiteStyle, Function}=By_Id) :: HypertextLiteral.Result
```

Style inline citations. `citations` is a Bond to [`References`](@ref), `bibtexpath` is path to the bibtex file. `content` can either be a [`CiteStyle`](@ref) or a Function, that is of the form  `(citeid::String, bibtexpath::String)::String`, whose output will replace the id in the citations

See also [`CiteStyle`](@ref)
