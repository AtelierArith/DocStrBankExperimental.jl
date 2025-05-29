```
svgstring()
```

現在および最近完了したSVG描画をSVGコマンドの文字列として返します。

SVG情報が利用できない場合は`""`を返します。

SVG文字列をグラフィックとして表示するには、Baseの`HTML()`関数を試してください。

```julia
...
HTML(svgstring())
```

Plutoノートブックでは、次のようにSVGを表示することもできます：

```julia
# using PlutoUI
...
PlutoUI.Show(MIME"image/svg+xml"(), svgstring())
```

（これにより、右クリックしてSVGを保存できます。）

## 例

この例では、Juliaロゴを描画することによって生成されたSVGコードを調べます。

```julia-repl
julia> Drawing(500, 500, :svg)

julia> origin()

julia> julialogo()

julia> finish()

julia> s = svgstring()

julia> eachmatch(r"rgb.*?;", s) |> collect
6-element Vector{RegexMatch}:
 RegexMatch("rgb(100%,100%,100%);")
 RegexMatch("rgb(0%,0%,0%);")
 RegexMatch("rgb(79.6%,23.5%,20%);")
 RegexMatch("rgb(25.1%,38.8%,84.7%);")
 RegexMatch("rgb(58.4%,34.5%,69.8%);")
 RegexMatch("rgb(22%,59.6%,14.9%);")
```

別の例として、`svgo`オプティマイザーでSVGファイルを後処理します。

```julia
@drawsvg begin
    background("midnightblue")
    fontface("JuliaMono-Regular")
    fontsize(20)
    sethue("gold")
    text("JuliaMono: a monospaced font ", halign=:center)
    text("with reasonable Unicode support", O + (0, 22), halign=:center)
end 500 150
write("txt.svg", svgstring())
# SVGを最小化
run(`svgo txt.svg -o txt-min.svg`)
```
