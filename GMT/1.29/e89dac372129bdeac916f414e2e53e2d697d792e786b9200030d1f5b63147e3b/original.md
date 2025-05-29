```
G = mat2grid(mat; reg=nothing, x=[], y=[], v=[], hdr=[], proj4::String="", wkt::String="",
             title::String="", rem::String="", cmd::String="", names::Vector{String}=String[],
             scale::Float32=1f0, offset::Float32=0f0, eqc=false)
```

Take a 2/3D `mat` array and a HDR 1x9 [xmin, xmax, ymin, ymax, zmin, zmax, reg, xinc, yinc] header descriptor and  return a grid GMTgrid type. Alternatively to HDR, provide a pair of vectors, `x` & `y`, with the X and Y coordinates. Optionally add a `v` vector with vertical coordinates if `mat` is a 3D array and one wants to create a $cube$. Optionally, the HDR arg may be omitted and it will computed from `mat` alone, but then x=1:ncol, y=1:nrow When HDR is not used, REG == nothing [default] means create a gridline registration grid and REG = 1, or REG="pixel" a pixel registered grid.

  * `eqc`: If true, it means we got a matrix representing a Equidistant Cylindrical projection but with no coords. The output grid will have global coordinates between [-180 180] and [-90 90]. The xinc and yinc will be computed from the `mat` size and and a guess of the registration type based on the if dims are even (pixel) or odd (grid). Override the registration guessing with the `reg` option. For non Earth bodies user must specify a `proj4` option.

For 3D arrays the `names` option is used to give a description for each layer (also saved to file when using a GDAL function).

The `scale` and `offset` options are used when `mat` is an Integer type and we want to save the grid with a scale/offset.  

---

Other methods of this function do:

```
G = mat2grid(val=0.0f; hdr=hdr_vec, reg=0, proj4::String="", wkt::String="", title::String="", rem::String="")
```

Create Float GMTgrid with size, coordinates and increment determined by the contents of the HDR var. This array, which is now MANDATORY, has either the same meaning as above OR, alternatively, containing only [xmin xmax ymin ymax xinc yinc] VAL is the value that will be fill the matrix (default VAL = Float32(0)). To get a Float64 array use, for example, VAL = 1.0 Any other non Float64 will be converted to Float32

```
Example: mat2grid(1, hdr=[0. 5 0 5 1 1])

G = mat2grid(f::Function, x, y; reg=nothing, proj4::String="", wkt::String="", epsg::Int=0, title::String="", rem::String="")
```

Where F is a function and X,Y the vectors coordinates defining it's domain. Creates a Float32 GMTgrid with size determined by the sizes of the X & Y vectors.

```
Example: f(x,y) = x^2 + y^2;  G = mat2grid(f, x = -2:0.05:2, y = -2:0.05:2)

G = mat2grid(f::String)
```

Where f is a pre-set function name. Currently available:

  * "ackley", "eggbox", "sombrero", "parabola" and "rosenbrock"

X,Y are vectors coordinates defining the function's domain, but default values are provided for each function. creates a Float32 GMTgrid.

```
Example: G = mat2grid("sombrero")
```
