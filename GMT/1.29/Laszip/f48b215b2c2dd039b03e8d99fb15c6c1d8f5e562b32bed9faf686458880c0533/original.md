```
lazwrite(FileName::AbstractString, xyz; grd_hdr=[], scaleX=nothing, scaleY=nothing, scaleZ=nothing, offX=nothing, offY=nothing, offZ=nothing)
```

Write XYZ data to a LIDAR laz (laszip compressed) or las format file.

```
Where:
	"FileName" Name of the output LIDAR file
	xyz  A Mx3 array with the point coordinates
```

### Example

To write the x,y,z data to file "lixo.laz" do:

```julia
	lazwrite("lixo.laz", xyz)
```
