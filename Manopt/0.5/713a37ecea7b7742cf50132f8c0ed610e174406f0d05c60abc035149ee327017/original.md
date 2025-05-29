```
asymptote_export_S2_signals(filename; points, curves, tangent_vectors, colors, kwargs...)
```

Export given `points`, `curves`, and `tangent_vectors` on the sphere $\mathbb S^2$ to Asymptote.

# Input

  * `filename`          a file to store the Asymptote code in.

# Keywaord arguments for the data

  * `colors=Dict{Symbol,Array{RGBA{Float64},1}}()`: dictionary of color arrays, indexed by symbols `:points`, `:curves` and `:tvector`, where each entry has to provide as least as many colors as the length of the corresponding sets.
  * `curves=Array{Array{Float64,1},1}(undef, 0)`: an `Array` of `Arrays` of points on the sphere, where each inner array is interpreted as a curve and is accompanied by an entry within `colors`.
  * `points=Array{Array{Float64,1},1}(undef, 0)`: an `Array` of `Arrays` of points on the sphere where each inner array is interpreted as a set of points and is accompanied by an entry within `colors`.
  * `tangent_vectors=Array{Array{Tuple{Float64,Float64},1},1}(undef, 0)`: an `Array` of `Arrays` of tuples, where the first is a points, the second a tangent vector and each set of vectors is accompanied by an entry from within `colors`.

# Keyword arguments for asymptote

  * `arrow_head_size=6.0`: size of the arrowheads of the tangent vectors
  * `arrow_head_sizes`  overrides the previous value to specify a value per `tVector`` set.
  * `camera_position=(1., 1., 0.)`: position of the camera in the Asymptote scene
  * `line_width=1.0`: size of the lines used to draw the curves.
  * `line_widths`       overrides the previous value to specify a value per curve and `tVector`` set.
  * `dot_size=1.0`: size of the dots used to draw the points.
  * `dot_sizes`         overrides the previous value to specify a value per point set.
  * `size=nothing`: a tuple for the image size, otherwise a relative size `4cm` is used.
  * `sphere_color=RGBA{Float64}(0.85, 0.85, 0.85, 0.6)`: color of the sphere the data is drawn on
  * `sphere_line_color=RGBA{Float64}(0.75, 0.75, 0.75, 0.6)`: color of the lines on the sphere
  * `sphere_line_width=0.5`: line width of the lines on the sphere
  * `target=(0.,0.,0.)`: position the camera points at
