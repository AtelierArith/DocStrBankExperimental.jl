```julia
Presentation(
    slides::Vector{Slide}=Slide[];
    title::String="My Presentation",
    author::String="PPTX.jl",
)
```

Type to contain the final presentation you want to write to .pptx.

If `isempty(slides)` then we add a first slide with the Title slide layout.

# Examples

```jldoctest
julia> using PPTX

julia> pres = Presentation(; title = "My Presentation", author = "PPTX.jl")
Presentation with 1 slide
 title is "My Presentation"
 author is "PPTX.jl"

```
