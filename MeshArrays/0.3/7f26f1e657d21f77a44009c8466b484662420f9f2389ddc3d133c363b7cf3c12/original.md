```
edge_path(name,mskCint,Γ)
```

Compute integration path that follows the outer edge of `mskCint>0`. 

```
Γ=GridLoad(ID=:LLC90)
mask=demo.extended_basin(demo.ocean_basins(),:Pac)
edge=edge_path("Pacific Ocean Edge",mask,Γ)
```
