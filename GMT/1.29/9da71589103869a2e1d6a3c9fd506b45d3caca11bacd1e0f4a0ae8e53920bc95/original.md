```
trisurf(in, kw...)
```

Plots the 3-D triangular surface.

The triangulation is defined by the points in a Mx3 matrix or a GMTdataset with data  x, y, z in the 3 first columns. The triangles are computed with a Delaunay triangulation done internaly. Since this is a `plot3d` *avatar* all options in this function are those of the `plot3d` program.

### Example

```julia
    x,y,z = GMT.peaks(N=45, grid=false);
	trisurf([x[:] y[:] z[:]], pen=0.5, show=true)
```
