ptn_3d(Pat::Pattern; dB::Bool = false, thr::Real = -50)

Plots a 3D radiation pattern. In 3D cases, `Pat.x` should be `theta` values in degrees, and `Pat.y` should be `phi` values in degrees. If dB scale is used for the data, please set the keyword `dB` to `true`. A threadsold value `thr` (max difference from the maximum value of the pattern) is used in case that `-Inf` appears in the dB scale data.

#### Arguments

  * `Pat`: A `Pattern`
  * `dB`: Boolean to plot if the pattern is in decibels (default: `false`)
  * `thr`: Threshold value for the plot if dB is true (default: `-50`)
