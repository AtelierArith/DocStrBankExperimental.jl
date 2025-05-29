When using Meshing.jl we can use the output of the $isosurface$ function, "verts, faces" as input to this function.

  * `F`:  A vector of Tuple{Int, Int, Int} with the body faces indices
  * `V`:  A vector of Tuple{Float64, Float64, Float64} with the body vertices

### Example

```julia
gyroid(v) = cos(v[1])*sin(v[2])+cos(v[2])*sin(v[3])+cos(v[3])*sin(v[1]);
gyroid_shell(v) = max(gyroid(v)-0.4,-gyroid(v)-0.4);
xr,yr,zr = ntuple(_ -> LinRange(0,pi*4,50), 3);
A = [gyroid_shell((x,y,z)) for x in xr, y in yr, z in zr];
A[1,:,:] .= 1e10; A[:,1,:] .= 1e10; A[:,:,1] .= 1e10; A[end,:,:] .= 1e10; A[:,end,:] .= 1e10; A[:,:,end] .= 1e10;
vts, fcs = isosurface(A, MarchingCubes());
FV = fv2fv(fcs, vts)
viz(FV, cmap=makecpt(T="0/1", cmap="darkgreen,lightgreen"))
```
