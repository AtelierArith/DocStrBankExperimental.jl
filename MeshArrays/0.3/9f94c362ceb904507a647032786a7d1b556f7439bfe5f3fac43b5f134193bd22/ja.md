```
knn(xgrid,ygrid::MeshArray,x,y::Array{T,1},k::Int)
```

xgrid,ygrid上の各点に対してx,yのk近傍点を見つけます。

```
lon=collect(0.1:0.5:2.1); lat=collect(0.1:0.5:2.1);
(f,i,j,c)=knn(Γ.XC,Γ.YC,lon,lat)
```
