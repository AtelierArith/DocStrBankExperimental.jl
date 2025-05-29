Extract the contents of a note as generic markdown. YAML headers and `dataview` blocks are omitted. wiki-style links are converted to standard markdown links with relative paths.

```julia
mdcontent(v, pg; quarto, omitdvtags, omittags)

```
