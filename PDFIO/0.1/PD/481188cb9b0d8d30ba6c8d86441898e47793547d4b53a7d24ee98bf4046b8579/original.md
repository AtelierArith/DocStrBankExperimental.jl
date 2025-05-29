```
    pdDocGetPageRange(doc::PDDoc, nums::AbstractRange{Int}) -> Vector{PDPage}
    pdDocGetPageRange(doc::PDDoc, label::AbstractString) -> Vector{PDPage}
```

Given a range of page numbers or a label returns an array of pages associated with it. For a detailed explanation on page labels, refer to the method `pdDocHasPageLabels`.

# Example

```
julia> pages = pdDocGetPageRange(doc, 1:4);

julia> typeof(pages)
Array{PDFIO.PD.PDPageImpl,1}

julia> length(pages)
4
```
