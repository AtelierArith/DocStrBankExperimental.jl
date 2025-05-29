```
html_element(name, content...=nothing; kwargs...)
```

Creates a new `EzXML.Node` with name `name`, containing `content`, and with attributes specified by `kwargs`.

# Example

```jldoctest
julia> import EzXML: prettyprint

julia> prettyprint(html_element("img"; src="https://millironx.com/images/charolette.jpg"))
<img src="https://millironx.com/images/charolette.jpg"/>

julia> prettyprint(html_element("span", "MillironX"; class="label-primary"))
<span class="label-primary">MillironX</span>
```
