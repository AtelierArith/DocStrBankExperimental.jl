```
visualize(coord_logger, boundary, out_filepath; <keyword arguments>)
```

Visualize a simulation as an animation.

This function is only available when GLMakie is imported. It can take a while to run, depending on the length of the simulation and the number of atoms.

# Arguments

  * `connections=Tuple{Int, Int}[]`: pairs of atoms indices to link with bonds.
  * `connection_frames`: the frames in which bonds are shown. Should be a list of   the same length as the number of frames, where each item is a list of   `Bool`s of the same length as `connections`. Defaults to always `true`.
  * `trails::Integer=0`: the number of preceding frames to show as transparent   trails.
  * `framerate::Integer=30`: the frame rate of the animation.
  * `color=:purple`: the color of the atoms. Can be a single color or a list of   colors of the same length as the number of atoms.
  * `connection_color=:orange`: the color of the bonds. Can be a single color or a   list of colors of the same length as `connections`.
  * `markersize=0.05`: the size of the atom markers, in the units of the data.
  * `linewidth=2.0`: the width of the bond lines.
  * `transparency=true`: whether transparency is active on the plot.
  * `show_boundary::Bool=true`: whether to show the bounding box as lines.
  * `boundary_linewidth=2.0`: the width of the boundary lines.
  * `boundary_color=:black`: the color of the boundary lines.
  * `kwargs...`: other keyword arguments are passed to the point plotting   function.
