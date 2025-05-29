```
argsout = lazread(FileName::AbstractString; out::String="xyz", type::DataType=Float64, class=0, startstop="1:end")
```

Read data from a LIDAR laz (laszip compressed) or las format file.

  * `FileName`: Name of the input LIDAR file.

### Keyword Arguments

  * `out`: Select what data to output. The default is "xyz" meaning that only these three are sent out.  Examples include: "xyz", "xy", "yx", "z", "xyzi", "xyzt", "xyzit", "xyzti", "xyzic" "xyzc", "RGB", "RGBI"  where 'i' stands for intensity (UInt16), 'c' for classification (Int8) and 't' for GPS time (Float64)
  * `type`: The float components (xyz) may be required in Float32. The default is Float64.
  * `startstop="start:stop"`: A string that restricts the output to the points from start to stop.
  * `class`: Restrict the output to the points belonging to the classification 'class' (an Integer).  This option implies two passes, with the first for counting the number of points in class.

### Returns

```
ARGSOUT is tuple with a Mx3 xyz array plus 't' and|or 'i' depending whether they were selected or not
```

### Example

To read the x,y,z,t data from file "lixo.laz" do:

```julia
	xyz, t = lazread("lixo.laz", "xyzt")
```
