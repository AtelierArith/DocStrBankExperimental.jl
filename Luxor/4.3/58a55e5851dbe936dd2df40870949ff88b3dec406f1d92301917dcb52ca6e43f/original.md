```
@imagematrix drawing-instructions [width=256] [height=256]
```

Create a drawing and return a matrix of the image.

This macro returns a matrix of pixels that represent the drawing produced by the vector graphics instructions. It uses the `image_as_matrix()` function.

The default drawing is 256 by 256 points.

You don't need `finish()` (the macro calls it), and it's not previewed by `preview()`.

```julia
julia> m = @imagematrix begin
               sethue("red")
               box(O, 20, 20, :fill)
           end 60 60;

julia> m[1220:1224]
5-element Array{ARGB32,1} with eltype ColorTypes.ARGB32:
 ARGB32(0.0N0f8,0.0N0f8,0.0N0f8,0.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
```

If, for some strange reason you want to draw the matrix as another Luxor drawing again, use code such as this:

```julia
m = @imagematrix begin
        sethue("red")
        box(O, 20, 20, :fill)
        sethue("blue")
        box(O, 10, 40, :fill)
    end 60 60

function convertmatrixtocolors(m)
    return convert.(Colors.RGBA, m)
end

function drawimagematrix(m)
    d = Drawing(500, 500, "/tmp/temp.png")
    origin()
    w, h = size(m)
    t = Tiler(500, 500, w, h)
    mi = convertmatrixtocolors(m)
    for (pos, n) in t
        c = mi[t.currentrow, t.currentcol]
        setcolor(c)
        box(pos, t.tilewidth -1, t.tileheight - 1, :fill)
    end
    finish()
    return d
end

drawimagematrix(m)
```

Transparency

The default value for the cells in an image matrix is transparent black. (Luxor's default color is opaque black.)

```julia
julia> @imagematrix begin
       end 2 2
2×2 reinterpret(ColorTypes.ARGB32, ::Matrix{UInt32}):
 ARGB32(0.0,0.0,0.0,0.0)  ARGB32(0.0,0.0,0.0,0.0)
 ARGB32(0.0,0.0,0.0,0.0)  ARGB32(0.0,0.0,0.0,0.0)
```

Setting the background to a partially or completely transparent value may give unexpected results:

```julia
julia> @imagematrix begin
           background(1, 0.5, 0.0, 0.5) # semi-transparent orange
       end 2 2
2×2 reinterpret(ColorTypes.ARGB32, ::Matrix{UInt32}):
 ARGB32(0.502,0.251,0.0,0.502)  ARGB32(0.502,0.251,0.0,0.502)
 ARGB32(0.502,0.251,0.0,0.502)  ARGB32(0.502,0.251,0.0,0.502)
```

here the semi-transparent orange color has been partially applied to the transparent background.

```julia
julia> @imagematrix begin
           sethue(1., 0.5, 0.0)
           paint()
       end 2 2
2×2 reinterpret(ColorTypes.ARGB32, ::Matrix{UInt32}):
 ARGB32(1.0,0.502,0.0,1.0)  ARGB32(1.0,0.502,0.0,1.0)
 ARGB32(1.0,0.502,0.0,1.0)  ARGB32(1.0,0.502,0.0,1.0)
```

picks up the default alpha of 1.0.
