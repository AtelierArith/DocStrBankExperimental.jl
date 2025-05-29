Plugin for enabling bibliographic citations in Documenter.jl.

```julia
bib = CitationBibliography(bibfile; style=:numeric)
```

instantiates a plugin object that must be passed as an element of the `plugins` keyword argument to [`Documenter.makedocs`](https://documenter.juliadocs.org/stable/lib/public/#Documenter.makedocs).

# Arguments

  * `bibfile`: the name of the [BibTeX](https://www.bibtex.com/g/bibtex-format/) file from which to read the data.
  * `style`: the style to use for the bibliography and all citations. The available built-in styles are `:numeric` (default), `:authoryear`, and `:alpha`. With user-defined styles, this may be an arbitrary name or object.

# Internal fields

The following internal fields are used by the citation pipeline steps. These should not be considered part of the stable API.

  * `entries`: dict of citation keys to entries in `bibfile`
  * `citations`: ordered dict of citation key to citation number
  * `page_citations`: dict of page file name to set of citation keys cited on page.
  * `anchor_map`: an [`AnchorMap`](https://documenter.juliadocs.org/stable/lib/internals/anchors/#Documenter.AnchorMap) object that keeps track of the link anchors for references in bibliography blocks
