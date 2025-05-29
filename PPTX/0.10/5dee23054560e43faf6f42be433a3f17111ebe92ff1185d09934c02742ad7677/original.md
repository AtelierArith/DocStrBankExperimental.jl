```julia
Slide(
    shapes::Vector{AbstractShape}=AbstractShape[];
    title::String="",
    layout::Int=1,
)
```

  * `shapes::Vector{AbstractShape}` shapes to add to the PowerPoint, can also be pushed afterwards
  * `title::String` title text placed inside the title textbox found in the slide layout
  * `layout::Int` which slide layout to use. Typically 1 is the title slide and 2 is the text slide.

Make a Slide for a powerpoint Presentation.

You can `push!` any `AbstractShape` types into this slide, such as a `TextBox` or `Picture`.

# Examples

```julia
julia> using PPTX

julia> slide = Slide(; title="Hello Title", layout=2)
Slide("Hello Title", PPTX.AbstractShape[], 0, 2)

julia> text = TextBox("Hello world!")
TextBox
 content is "Hello world!"
 offset_x is 1800000 EMUs
 offset_y is 1800000 EMUs
 size_x is 1440000 EMUs
 size_y is 1080000 EMUs

julia> push!(slide, text);

julia> slide
Slide("Hello Title", PPTX.AbstractShape[TextBox], 0, 2)

```
