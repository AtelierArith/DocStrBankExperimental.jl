```
@savesvg begin
    body
end w h
```

`@drawsvg`と似ていますが、描画の生SVGコードを文字列として返します。`svgstring`を使用します。

`@draw`（PNG）とは異なり、デフォルトでは背景はありません。

この例では、生成されたSVGから色の値をスキャンします：

```julia-repl
julia> s = @savesvg begin
           julialogo()
       end

julia> eachmatch(r"rgb.*?;", s) |> collect
5-element Vector{RegexMatch}:
 RegexMatch("rgb(0%,0%,0%);")
 RegexMatch("rgb(25.1%,38.8%,84.7%);")
 RegexMatch("rgb(22%,59.6%,14.9%);")
 RegexMatch("rgb(58.4%,34.5%,69.8%);")
 RegexMatch("rgb(79.6%,23.5%,20%);")
```
