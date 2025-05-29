```
CurvilinearGrid3D(x, y, z, nhalo::Int; backend=CPU(), discretization_scheme=:MEG6, on_bc=nothing, is_static=false, is_orthogonal=false, tiles=nothing, make_uniform=false)
```

3Dのx/y/z座標の3D配列を使用して、曲線格子を構築します。
