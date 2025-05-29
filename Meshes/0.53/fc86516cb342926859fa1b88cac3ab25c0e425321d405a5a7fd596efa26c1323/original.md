```
Slice(x=(xmin, xmax), y=(ymin, ymax), z=(zmin, zmax))
Slice(lat=(latmin, latmax), lon=(lonmin, lonmax))
```

Retain the domain elements within `x` limits [`xmax`,`xmax`], `y` limits [`ymax`,`ymax`] and `z` limits [`zmin`,`zmax`] in length units (default to meters), or within `lat` limits [`latmin`,`latmax`] and `lon` limits [`lonmin`,`lonmax`] in degree units.

## Examples

```julia
Slice(x=(1000km, 3000km))
Slice(x=(1000km, 2000km), y=(2000km, 5000km))
Slice(lon=(0°, 90°))
Slice(lon=(0°, 45°), lat=(0°, 45°))
```
