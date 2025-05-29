```
html(md::Markdown.MD; context::Module = @__MODULE__, status::Int = 200, headers::Genie.Renderer.HTTPHeaders = Genie.Renderer.HTTPHeaders(), layout::Union{String,Nothing} = nothing, forceparse::Bool = false, vars...) :: Genie.Renderer.HTTP.Response
```

Markdown view rendering
