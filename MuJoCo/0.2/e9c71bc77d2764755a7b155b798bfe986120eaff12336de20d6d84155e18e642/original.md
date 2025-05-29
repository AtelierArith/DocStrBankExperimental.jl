```
mj_zeros([element_type=mjtNum], dims...)
```

Allocates an array full of zeros, compatible with the underlying MuJoCo C API.

The C API treats arrays as row-major, while by default arrays in Julia are column-major. This function will create an array which is accessed in a row-major way, but can be treated by a normal  array in your Julia code.

# Arguments

  * **element_type**: The element type of the array. Defaults to mjtNum (typically Float64).
  * **dims**: The dimensionality of output array. Can either be a tuple of integers or a series of integers.
