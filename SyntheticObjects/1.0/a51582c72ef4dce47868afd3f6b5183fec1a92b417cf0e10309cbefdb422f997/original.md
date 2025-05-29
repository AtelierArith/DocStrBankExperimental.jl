```
object_3D([DataType], sz, radius=0.8, center=sz.÷2 .+1; thickness=0.8)
```

Create a 3D object with a hollow sphere (cell membrane), another hollow sphere (nucleus), a hollow small sphere (vesicle), a filled small sphere (), and a line.

# Arguments

  * `DataType`: The optional datatype of the output array. Default is Float32.
  * `sz`: A vector of integers representing the size of the object. Default is (128, 128, 128).
  * `radius`: A float (or tuple) representing the relative radius of the cell sphere.
  * `center`: A tuple representing the center of the object.
  * `thickness`: A float representing the thickness of the membranes in pixels. Default is 0.8.
