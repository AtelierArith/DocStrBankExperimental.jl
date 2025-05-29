```
WebRenderable(body::String, content_type::Symbol)
```

Creates a new instance of `WebRenderable` with `body` as the body of the response and `content_type` as the content type, no headers, and 200 status code.

#Examples

```jldoctest
julia> Genie.Renderer.WebRenderable("hello", :json)
Genie.Renderer.WebRenderable("hello", :json, 200, Dict{String,String}())
```
