Meshing.jlを使用する際、$isosurface$関数の出力である"verts, faces"をこの関数の入力として使用できます。

  * `F`:  ボディの面のインデックスを持つTuple{Int, Int, Int}のベクトル
  * `V`:  ボディの頂点を持つTuple{Float64, Float64, Float64}のベクトル

### 例

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
