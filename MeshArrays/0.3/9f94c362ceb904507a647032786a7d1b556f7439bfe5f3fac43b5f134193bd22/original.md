```
knn(xgrid,ygrid::MeshArray,x,y::Array{T,1},k::Int)
```

Find k nearest neighbors to each point in x,y on xgrid,ygrid

```
lon=collect(0.1:0.5:2.1); lat=collect(0.1:0.5:2.1);
(f,i,j,c)=knn(Γ.XC,Γ.YC,lon,lat)
```
