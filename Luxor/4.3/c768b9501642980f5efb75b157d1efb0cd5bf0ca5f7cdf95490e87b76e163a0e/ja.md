```
readsvg(str)
```

SVG画像を読み込みます。`str`はパス名または純粋なSVGコードです。これにより、`placeimage()`で現在の描画に配置するのに適したSVG画像オブジェクトが返されます。

SVGファイルを配置する：

```julia
@draw begin
    mycoollogo = readsvg("mylogo.svg")
    placeimage(mycoollogo)
end
```

SVGコードを配置する：

```julia
# from https://github.com/edent/SuperTinyIcons
julialogocode = """<svg xmlns="http://www.w3.org/2000/svg"
    aria-label="Julia" role="img"
    viewBox="0 0 512 512">
    <rect width="512" height="512" rx="15%" fill="#fff"/>
    <circle fill="#389826" cx="256" cy="137" r="83"/>
    <circle fill="#cb3c33" cx="145" cy="329" r="83"/>
    <circle fill="#9558b2" cx="367" cy="329" r="83"/>
</svg>"""

@draw begin
    julia_logo = readsvg(julialogocode)
    placeimage(julia_logo, centered=true)
end
```
