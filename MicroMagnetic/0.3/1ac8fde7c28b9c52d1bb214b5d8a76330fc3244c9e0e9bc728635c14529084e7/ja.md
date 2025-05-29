```
update_anis(sim::MicroSim, Ku::NumberOrArrayOrFunction; name = "anis")
```

名前に従って異方性定数 Ku を更新します。

例:

```julia
    mesh = FDMesh(nx=200, ny=200, nz=12, dx=5e-9, dy=5e-9, dz=5e-9)
    sim = Sim(mesh)
    add_anis(sim, 3e4, axis = (0,0,1), name="K1")
    add_anis(sim, 1e5, axis = (1,0,0), name="K2")
    update_anis(sim, 5e4, name="K2")  #異方性 K2 を更新
```
