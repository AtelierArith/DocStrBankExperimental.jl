```
Transformation(source_epsg, target_epsg; threaded=true, always_xy=false, proj_only=false)
```

Create a Transformation that is a pipeline between two known coordinate reference systems. Transformation implements the [CoordinateTransformations.jl](https://github.com/JuliaGeometry/CoordinateTransformations.jl) API.

To do the transformation on coordinates, call an instance of this struct like a function. See below for an example. These functions accept either 2 numbers or two vectors of numbers.

`source_crs` and `target_crs` must be an EPSG authority code (see https://epsg.io/), like  "EPSG:3413" or 3413::EPSG. The created pipeline will expect that the coordinates respect  the axis order and axis unit of the official definition (so for example,  for EPSG:4326, with latitude first and longitude next, in degrees). Similarly, when using  that syntax for a target CRS, output values will be emitted according to the official  definition of this CRS. This behavior can be overruled by passing `always_xy=true`.

`threaded` turns on an off multi-threading.

`always_xy` can optionally fix the axis orderding to x,y or lon,lat order. By default it is `false`, meaning the order is defined by the authority in charge of a given coordinate reference system, as explained in [this PROJ FAQ entry](https://proj.org/faq.html#why-is-the-axis-ordering-in-proj-not-consistent).

`proj_only` can optionally only use Proj.jl for Transformations even when a  FastGeoProjection is available. By default Proj.jl is only used when a FastGeoProjection is  not avaiable 

# Examples

```julia
julia> trans = Proj.Transformation("EPSG:4326", "EPSG:28992", always_xy=true)
Transformation
    source: WGS 84 (with axis order normalized for visualization)
    target: Amersfoort / RD New

julia> trans(5.39, 52.16)  # this is in lon,lat order, since we set always_xy to true
(155191.3538124342, 463537.1362732911)
```
