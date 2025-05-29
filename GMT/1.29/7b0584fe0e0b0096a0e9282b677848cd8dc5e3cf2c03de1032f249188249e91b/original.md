```
FV = extrude(shape::Matrix{<:AbstractFloat}, h; base=0.0, closed=true) -> GMTfv
```

Create an extruded 2D/3D shape.

### Args

  * `shape`: The shape to extrude. It can be a 2D polygon or a 3D polygon defined by a Mx2 or Mx3 matrix or a `GMTdataset`
  * `h`: The height of the extrusion. Same units as in `shape`.

### Kwargs

  * `base`: The base height of the 2D shape to extrude. Default is 0. Ignored if the shape is a 3D polygon.
  * `closed`: If true (the default), close the shape at top and bottom.

### Example

Extrude the Swisserland

```julia
	Dsw = coast(dump=true, DCW=(country=:CH, file=:ODS));	# Get the Swiss border
	FV = extrude(Dsw, 0.2)
	viz(FV)
```
