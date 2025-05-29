```
pluralize(noun::String)
```

与えられた英語の名詞の単数形の複数形を返します。

この関数は特定のヒューリスティックを使用しているため、常に正しい複数形を取得できるわけではありません。しかし、ほとんどのケースでは十分に機能します。

# 例

```jldoctest
julia> pluralize("generator")
"generators"

julia> pluralize("variety")
"varieties"
```
