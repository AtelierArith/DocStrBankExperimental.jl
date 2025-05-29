```
html_element(name, content...=nothing; kwargs...)
```

`name`という名前の新しい`EzXML.Node`を作成し、`content`を含み、`kwargs`で指定された属性を持ちます。

# 例

```jldoctest
julia> import EzXML: prettyprint

julia> prettyprint(html_element("img"; src="https://millironx.com/images/charolette.jpg"))
<img src="https://millironx.com/images/charolette.jpg"/>

julia> prettyprint(html_element("span", "MillironX"; class="label-primary"))
<span class="label-primary">MillironX</span>
```
