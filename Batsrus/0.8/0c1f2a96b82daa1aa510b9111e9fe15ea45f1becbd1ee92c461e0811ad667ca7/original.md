```
 readtecdata(file; verbose=false)
```

Return header, data and connectivity from BATSRUS Tecplot outputs. Both 2D and 3D binary and ASCII formats are supported.

# Examples

```
file = "3d_ascii.dat"
head, data, connectivity = readtecdata(file)
```
