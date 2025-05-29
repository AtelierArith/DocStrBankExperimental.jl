```
RenderableText(text::String; width::Union{Nothing, Int, Symbol}=nothing)
```

Construct a `RenderableText` out of a string.

The text is resized to fit the given width. Optionally `justify`  can be used to set the text justification style ∈ (:left, :center, :right, :justify).
