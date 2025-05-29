```
parse(Colorant, desc)
```

Parse a color description.

This parses a subset of HTML/CSS color specifications. In particular, everything is supported but: `currentColor`.

It does support named colors (though it uses X11 named colors, which are slightly different than W3C named colors in some cases), `rgb()`, `hsl()`, `#RGB`, and `#RRGGBB` syntax.

# Arguments

  * `Colorant`: literal Colorant
  * `desc`: color name or description

A literal Colorant will parse according to the `desc` string (usually returning an `RGB`); any more specific choice will return a color of the specified type.

# Returns

  * an `RGB{N0f8}` color, or
  * an `HSL` color if `hsl(h, s, l)` was used
  * an `RGBA` color if `rgba(r, g, b, a)` was used
  * an `HSLA` color if `hsla(h, s, l, a)` was used
  * an `ARGB{N0f8}` color if `0xAARRGGBB`/`0xARGB` was used
  * a specific `Colorant` type as specified in the first argument

!!! note "Note for X11 named colors"
    The X11 color names with spaces (e.g. "sea green") are not recommended because they are not allowed in the SVG/CSS.


!!! note "Note for hex notations"
    You can parse not only the CSS-style hex notations `#RRGGBB`/`#RGB`, but also `0xRRGGBB`/`0xRGB`.

    You can also parse the 8-digit or 4-digit hex notation into an RGB color with alpha. However, the result depends on the prefix (i.e. `#` or `0x`).

    ```julia-repl
    julia> parse(Colorant, "#FF8800AA") # transparent orange
    RGBA{N0f8}(1.0,0.533,0.0,0.667)

    julia> parse(Colorant, "0xFF8800AA") # opaque purple
    ARGB{N0f8}(0.533,0.0,0.667,1.0)
    ```

