```
@eps drawing-instructions [width] [height] [filename]
```

Create and preview an EPS drawing, optionally specifying width and height (the default is 600 by 600). The file is saved in the current working directory as `filename` if supplied, or `luxor-drawing(timestamp).eps`.

On some platforms, EPS files are converted automatically to PDF when previewed.

These 'short-cut' macros are designed for convenience and to save typing. The macro `@draw ⟦ body ⟧ width height filename` expands to:

```julia
Drawing(width, height, filename)
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
@eps circle(O, 20, :fill)
```

```julia
@eps circle(O, 20, :fill) 400
```

```julia
@eps circle(O, 20, :fill) 400 1200
```

```julia
@eps circle(O, 20, :fill) 400 1200 "/tmp/A0-version"
```

```julia
@eps circle(O, 20, :fill) 400 1200 "/tmp/A0-version.eps"
```

```julia
@eps begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@eps begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
