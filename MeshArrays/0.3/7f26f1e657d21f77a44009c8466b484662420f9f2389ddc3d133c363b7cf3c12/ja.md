```
edge_path(name,mskCint,Γ)
```

`mskCint>0`の外側のエッジに沿った積分パスを計算します。

```
Γ=GridLoad(ID=:LLC90)
mask=demo.extended_basin(demo.ocean_basins(),:Pac)
edge=edge_path("Pacific Ocean Edge",mask,Γ)
```
