```
WebRenderable(body::String)
```

Creates a new instance of `WebRenderable` with `body` as the body of the response and default content type, no headers, and 200 status code.

#Examples

```jldoctest
julia> Genie.Renderer.WebRenderable("hello")
Genie.Renderer.WebRenderable("hello", :html, 200, Dict{String,String}())
```
