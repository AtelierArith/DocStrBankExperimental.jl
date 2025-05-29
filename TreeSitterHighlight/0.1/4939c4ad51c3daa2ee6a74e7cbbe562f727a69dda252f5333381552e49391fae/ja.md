```
HighlightBuffer(names_attributes::Dict{String,String})
```

HighlightBufferは、構文ハイライトを実行するために必要なオブジェクトです。namesパラメータは、spanでラップされるべきキャプチャグループを表します。attributes要素は、これらのspanのそれぞれのspanに挿入されるべき対応するHTML属性に対応します。

```julia
julia> highlighter = Highlighter(Dict(
           "keyword" => "class=keyword",
       ))
Highlighter(Language[])
```
