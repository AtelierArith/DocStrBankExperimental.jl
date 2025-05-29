```
@draw drawing-instructions [width] [height]
```

Create and preview an PNG drawing, optionally specifying width and height (the default is 600 by 600). The drawing is stored in memory, not in a file on disk.

These 'short-cut' macros are designed for convenience and to save typing. The macro `@draw ⟦ body ⟧ width height` expands to:

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

`@draw circle(O, 20, :fill)`

```julia
@draw circle(O, 20, :fill) 400
```

```julia
@draw circle(O, 20, :fill) 400 1200
```

```julia
@draw begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@draw begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
