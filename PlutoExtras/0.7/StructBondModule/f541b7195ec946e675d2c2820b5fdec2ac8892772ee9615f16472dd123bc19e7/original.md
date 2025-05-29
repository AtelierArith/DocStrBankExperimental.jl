A widget to select one subwidget out of an array of provided elements, which can be either `StructBond` or the resulting form `transformed_value(f, ::StructBond)`.

This will show a selection dropdown to choose the subwidget to display and use for generating the StructBondSelect output when coupled with `@bind`.

See the extended help below for a GIF example or the [docs page](https://disberd.github.io/PlutoExtras.jl/stable/structbond/#StructBondSelect) for a video one.

## Constructor

```julia
StructBondSelect(els::Vector[, selectors::Vector{String}]; description = "StructBondSelect", default_idx = 1, selector_text = "Selector")
```

### Arguments

  * `els`: A vector of `StructBond` or `transformed_value(f, ::StructBond)` elements.
  * `selectors`: A vector of strings to be used as the names to select upon. If not provided, the names will be taken from the `description` of the provided `StructBond` elements.

### Keyword Arguments

  * `description`: A string to be used as the description of the widget, defaults to `"StructBondSelect"`.
  * `default_idx`: The index of the element to be selected by default for display/output, defaults to `1`.
  * `selector_text`: The text to be displayed next to the selector dropdown, defaults to `"Selector"`.

# Extended Help

See this image for a visual example: ![structbondselect-example](https://private-user-images.githubusercontent.com/12846528/435671705-91ff7e4a-2b4c-4688-8f2b-ea53a622dd04.gif?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDUyNDAzMTgsIm5iZiI6MTc0NTI0MDAxOCwicGF0aCI6Ii8xMjg0NjUyOC80MzU2NzE3MDUtOTFmZjdlNGEtMmI0Yy00Njg4LThmMmItZWE1M2E2MjJkZDA0LmdpZj9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA0MjElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwNDIxVDEyNTMzOFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTYwMmI1ZTYyNGQ1NDMyZGNlZTE3NzljMjJlNWQyOTU5ODUyMDdiODkzYWQxNDRmNzEwZjYxZmEzNTgwZDUyYmEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.L9eC42c4-Gz0tpjzGgF95LhOvcrGAEPOkJ71HhiICrs)

See also: [`StructBond`](@ref), [`@NTBond`](@ref)
