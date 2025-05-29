```
WebRenderable(body::String)
```

`body`をレスポンスのボディとして、デフォルトのコンテンツタイプ、ヘッダーなし、ステータスコード200で新しい`WebRenderable`のインスタンスを作成します。

#例

```jldoctest
julia> Genie.Renderer.WebRenderable("hello")
Genie.Renderer.WebRenderable("hello", :html, 200, Dict{String,String}())
```
