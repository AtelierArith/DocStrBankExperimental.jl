```
display_bibliography(bibtexpath::String, citations) ::HypertextLiteral.Result
```

`bibtexpath`と`citations`の参照BibTexファイルからすべての引用された参考文献を返します。また、[`show_abstract`](@ref)と一緒に使用するために変数にバインドすることもできます。

他に[`@cite_str`](@ref)、[`References`](@ref)も参照してください。
