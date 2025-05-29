```
WebRenderable(; body::String = "", content_type::Symbol = DEFAULT_CONTENT_TYPE,
                status::Int = 200, headers::HTTPHeaders = HTTPHeaders())
```

キーワード引数として渡された値を使用して、新しい`WebRenderable`のインスタンスを作成します。

#例

```jldoctest
julia> Genie.Renderer.WebRenderable()
Genie.Renderer.WebRenderable("", :html, 200, Dict{String,String}())

julia> Genie.Renderer.WebRenderable(body = "bye", content_type = :javascript, status = 301, headers = Dict("Location" => "/bye"))
Genie.Renderer.WebRenderable("bye", :javascript, 301, Dict("Location" => "/bye"))
```
