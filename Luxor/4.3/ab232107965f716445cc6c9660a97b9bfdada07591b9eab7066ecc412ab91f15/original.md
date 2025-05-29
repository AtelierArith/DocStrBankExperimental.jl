```
@pdf drawing-instructions [width] [height] [filename]
```

Create and preview an PDF drawing, optionally specifying width and height (the default is 600 by 600). The file is saved in the current working directory as `filename` if supplied, or `luxor-drawing(timestamp).pdf`.

These 'short-cut' macros are designed for convenience and to save typing. The macro `@pdf ⟦ body ⟧ width height` expands to:

```julia
Drawing(width, height, :pdf)
origin()
background("white")
sethue("black")
⟦ body ⟧
finish()
preview()
```

For full control of the drawing construction, use these functions directly rather than the short-cut macros.

### Examples

```julia
@pdf circle(O, 20, :fill)
```

```julia
@pdf circle(O, 20, :fill) 400
```

```julia
@pdf circle(O, 20, :fill) 400 1200
```

```julia
@pdf circle(O, 20, :fill) 400 1200 "/tmp/A0-version"
```

```julia
@pdf circle(O, 20, :fill) 400 1200 "/tmp/A0-version.pdf"
```

```julia
@pdf begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@pdf begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
