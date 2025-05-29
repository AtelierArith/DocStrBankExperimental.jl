A vectorized function that returns the value of the look ahead estimate at the values in the array `y`.

##### Arguments

  * `l::LAE`: Instance of `LAE` type
  * `y::Array`: Array that becomes the `y` in `l.p(l.x, y)`

##### Returns

  * `psi_vals::Vector`: Density at `(x, y)`
