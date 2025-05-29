```
draw_line!(arr, start, stop; thickness=0.5, intensity=one(eltype(arr)))
```

Draw a line in a 3D array by adding a Gaussian profile to the array.

#Arguments:

  * `arr::Array`: A 3D array to which the line will be added.
  * `start`: The starting point of the line as a tuple.
  * `stop`: The stopping point of the line as a tuple.
  * `thickness`: The thickness of the line. Default is 0.5.
  * `intensity::Float64`: The intensity of the line. Default is 1.0.
