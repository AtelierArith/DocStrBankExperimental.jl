```
readsvg(str)
```

Read an SVG image. `str` is either pathname or pure SVG code. This returns an SVG image object suitable for placing on the current drawing with `placeimage()`.

Placing an SVG file:

```julia
@draw begin
    mycoollogo = readsvg("mylogo.svg")
    placeimage(mycoollogo)
end
```

Placing SVG code:

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
