```
    pdPageGetMediaBox(page::PDPage) -> CDRect{Float32}
    pdPageGetCropBox(page::PDPage) -> CDRect{Float32}
```

```
Returns the media box associated with the page. See 14.11.2 PDF 1.7 Spec.
```

It's typically, the designated size of the paper for the page. When a crop box is not defined, it defaults to the media box.

# Example

```
julia> pdPageGetMediaBox(page)
Rect:[0.0 0.0 595.0 792.0]

julia> pdPageGetCropBox(page)
Rect:[0.0 0.0 595.0 792.0]
```
