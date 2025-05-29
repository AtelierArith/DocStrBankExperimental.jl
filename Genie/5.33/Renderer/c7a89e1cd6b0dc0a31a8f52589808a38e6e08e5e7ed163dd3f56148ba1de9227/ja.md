```
WebRenderable(body::String, content_type::Symbol)
```

`body`をレスポンスのボディとして、`content_type`をコンテンツタイプとして、新しい`WebRenderable`のインスタンスを作成します。ヘッダーはなく、ステータスコードは200です。

#例

```jldoctest
julia> Genie.Renderer.WebRenderable("hello", :json)
Genie.Renderer.WebRenderable("hello", :json, 200, Dict{String,String}())
```
