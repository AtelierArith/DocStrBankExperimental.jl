```
html(content...=nothing; kwargs...)
```

`content`で満たされた新しいHTMLドキュメントを作成します。

# 例

```jldoctest
julia> import EzXML: prettyprint

julia> prettyprint(html())
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!DOCTYPE html SYSTEM "about:legacy-compat">
<html/>
```
