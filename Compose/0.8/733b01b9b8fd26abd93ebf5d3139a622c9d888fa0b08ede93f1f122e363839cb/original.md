```
context(x0=0.0w, y0=0.0h, width=1.0w, height=1.0h;
        units=nothing,
        rotation=nothing, mirror=nothing, shear=nothing,
        withjs=false, withoutjs=false,
        minwidth=nothing, minheight=nothing,
        order=0, clip=false, raster=false) -> Context
```

Create a node in the tree structure that defines a graphic.  Use [`compose`](@ref) to connect child nodes to a parent node.  See also [`Rotation`](@ref), [`Mirror`](@ref), and [`Shear`](@ref).

# Arguments

  * `units`: the coordinate system for the context, defined by a [`UnitBox`](@ref).
  * `order`: the Z-order of this context relative to its siblings.
  * `clip`:  clip children of the canvas by its bounding box if true.
  * `withjs`: ignore this context and everything under it if we are not drawing to the SVGJS backend.
  * `withoutjs`: ignore this context if we *are* drawing on the SVGJS backend.
  * `raster`: if possible, render this subtree as a bitmap. This requires the Cairo. If Cairo isn't available, the default rendering is used.
  * `minwidth` and `minheight`: the minimum size needed to be drawn correctly, in millimeters.
