```
style_citations(citations, bibtexpath::String; css::Union{CiteCSS, HypertextLiteral.Result}=Superscript, content::Union{CiteStyle, Function}=By_Id) :: HypertextLiteral.Result
```

インライン引用をスタイル設定します。`citations` は [`References`](@ref) への Bond であり、`bibtexpath` は bibtex ファイルへのパスです。`content` は [`CiteStyle`](@ref) または関数であり、その形式は `(citeid::String, bibtexpath::String)::String` で、出力は引用内の id を置き換えます。

詳細は [`CiteStyle`](@ref) を参照してください。
