```julia
Presentation(
    slides::Vector{Slide}=Slide[];
    title::String="私のプレゼンテーション",
    author::String="PPTX.jl",
)
```

Type to contain the final presentation you want to write to .pptx.

If `isempty(slides)` then we add a first slide with the Title slide layout.

# Examples

```jldoctest
julia> using PPTX

julia> pres = Presentation(; title = "私のプレゼンテーション", author = "PPTX.jl")
Presentation with 1 slide
 title is "私のプレゼンテーション"
 author is "PPTX.jl"

```
