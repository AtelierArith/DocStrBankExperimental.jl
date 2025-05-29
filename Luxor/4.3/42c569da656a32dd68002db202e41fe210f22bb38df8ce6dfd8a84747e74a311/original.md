```
@svg drawing-instructions [width] [height] [filename]
```

Create and preview an SVG drawing, optionally specifying width and height (the default is 600 by 600). The file is saved in the current working directory as `filename` if supplied, or `luxor-drawing-(timestamp).svg`.

### Examples

```julia
@svg circle(O, 20, :fill)
```

```julia
@svg circle(O, 20, :fill) 400
```

```julia
@svg circle(O, 20, :fill) 400 1200
```

```julia
@svg circle(O, 20, :fill) 400 1200 "/tmp/test"
```

```julia
@svg circle(O, 20, :fill) 400 1200 "/tmp/test.svg"
```

```julia
@svg begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end
```

```julia
@svg begin
    setline(10)
    sethue("purple")
    circle(O, 20, :fill)
end 1200 1200
```
