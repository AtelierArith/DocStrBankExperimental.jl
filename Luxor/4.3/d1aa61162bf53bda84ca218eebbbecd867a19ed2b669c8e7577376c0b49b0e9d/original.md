```
@png drawing-instructions [width] [height] [filename]
```

Create and preview an PNG drawing, optionally specifying width and height (the default is 600 by 600). The file is saved in the current working directory as `filename`, if supplied, or `luxor-drawing(timestamp).png`.

These 'short-cut' macros are designed for convenience and to save typing. The macro `@png ⟦ body ⟧ width height` expands to:

```julia
Drawing(width, height, :png)
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
@png circle(O, 20, :fill)
```

```julia
@png circle(O, 20, :fill) 400
```

```julia
@png circle(O, 20, :fill) 400 1200
```

```julia
@png circle(O, 20, :fill) 400 1200 "/tmp/round"
```

```julia
@png circle(O, 20, :fill) 400 1200 "/tmp/round.png"
```

```julia
@png begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@png begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
