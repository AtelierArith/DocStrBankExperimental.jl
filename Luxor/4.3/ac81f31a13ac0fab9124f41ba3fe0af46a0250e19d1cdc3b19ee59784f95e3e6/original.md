Create a new drawing, and optionally specify file type (PNG, PDF, SVG, EPS), file-based or in-memory, and dimensions.

```
Drawing(width=600, height=600, file="luxor-drawing.png")
```

# Extended help

```julia
Drawing()
```

creates a drawing, defaulting to PNG format, default filename "luxor-drawing.png", default size 800 pixels square.

You can specify dimensions, and assume the default output filename:

```julia
Drawing(400, 300)
```

creates a drawing 400 pixels wide by 300 pixels high, defaulting to PNG format, default filename "luxor-drawing.png".

```julia
Drawing(400, 300, "my-drawing.pdf")
```

creates a PDF drawing in the file "my-drawing.pdf", 400 by 300 pixels.

```julia
Drawing(1200, 800, "my-drawing.svg")
```

creates an SVG drawing in the file "my-drawing.svg", 1200 by 800 pixels.

```julia
Drawing(width, height, surfacetype | filename)
```

creates a new drawing of the given surface type (e.g. :svg, :png), storing the picture only in memory if no filename is provided.

```julia
Drawing(1200, 1200/Base.Mathconstants.golden, "my-drawing.eps")
```

creates an EPS drawing in the file "my-drawing.eps", 1200 wide by 741.8 pixels (= 1200 ÷ ϕ) high. Only for PNG files must the dimensions be integers.

```julia
Drawing("A4", "my-drawing.pdf")
```

creates a PDF drawing in ISO A4 size (595 wide by 842 high) in the file "my-drawing.pdf". Other sizes available are: "A0", "A1", "A2", "A3", "A4", "A5", "A6", "Letter", "Legal", "A", "B", "C", "D", "E". Append "landscape" to get the landscape version.

```julia
Drawing("A4landscape")
```

creates the drawing A4 landscape size.

PNG and PDF default to transparent backgrounds, unless you specify one using `background()`.

```julia
Drawing(width, height, :image)
```

creates the drawing in an image buffer in memory. You can obtain the data as a matrix with `image_as_matrix()`.

```julia
Drawing(width, height, :rec)
```

creates the drawing in a recording surface in memory. `snapshot(fname, ...)` to any file format and bounding box, or render as pixels with `image_as_matrix()`.

```julia
Drawing(width, height, strokescale=true)
```

creates the drawing and enables stroke scaling (strokes will be scaled according to the current transformation). (Stroke scaling is disabled by default.)

```julia
Drawing(img, strokescale=true)
```

creates the drawing from an existing image buffer of type `Matrix{Union{RGB24,ARGB32}}`, e.g.:

```julia
using Luxor, Colors
buffer=zeros(ARGB32, 100, 100)
d=Drawing(buffer)
```
