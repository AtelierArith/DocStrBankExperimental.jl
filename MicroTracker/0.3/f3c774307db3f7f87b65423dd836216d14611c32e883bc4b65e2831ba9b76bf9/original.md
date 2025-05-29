```
add_useful_columns(linked_data::AbstractDataFrame, linking_settings::NamedTuple)
```

After linking, add some useful columns to the dataframe, like include dx, dy, dp (speed), and size measurements in microns. 

Uses the [`numerical_derivative`](@ref) and [`total_displacement`](@ref) functions.

# Definitions

  * `particle_unique` : a string which uniquely identifies a particle. This is a combination of the filename and the particle number.
  * `dx` : numerical derivative of `x`, i.e. instantaneous velocity in the x direction. Units of pixels/frame.
  * `dy` : numerical derivative of `y`, i.e. instantaneous velocity in the y direction. Units of pixels/frame.
  * `dp` : instantaneous speed. √(dx^2 + dy^2). Units of pixels/frame.
  * `dx_um` : dx converted to µm/s.
  * `dy_um` : dy converted to µm/s.
  * `dp_um` : dp converted to µm/s.
  * `total_displacement_um` : total displacement of the microbot. Constant on every row, since this is a total. Units of µm.
  * `Area_um` : area of the microbot. Units of µm^2.
  * `time` : time, converted from the frame column. Units of seconds.
  * `Major_um` : major axis of the fit ellipse of the microbot. Units of µm.
  * `Minor_um` : minor axis of the fit ellipse of the microbot. Units of µm.
