```
WebRenderable(wr::WebRenderable, status::Int, headers::HTTPHeaders)
```

渡された引数で `status` と `headers` フィールドを上書きして `wr` を返します。

#例

```jldoctest
julia> Genie.Renderer.WebRenderable(Genie.Renderer.WebRenderable(body = "good morning", content_type = :javascript), 302, Dict("Location" => "/morning"))
Genie.Renderer.WebRenderable("good morning", :javascript, 302, Dict("Location" => "/morning"))
```
