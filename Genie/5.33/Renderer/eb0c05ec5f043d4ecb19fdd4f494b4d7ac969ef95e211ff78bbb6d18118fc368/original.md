```
WebRenderable(wr::WebRenderable, status::Int, headers::HTTPHeaders)
```

Returns `wr` overwriting its `status` and `headers` fields with the passed arguments.

#Examples

```jldoctest
julia> Genie.Renderer.WebRenderable(Genie.Renderer.WebRenderable(body = "good morning", content_type = :javascript), 302, Dict("Location" => "/morning"))
Genie.Renderer.WebRenderable("good morning", :javascript, 302, Dict("Location" => "/morning"))
```
