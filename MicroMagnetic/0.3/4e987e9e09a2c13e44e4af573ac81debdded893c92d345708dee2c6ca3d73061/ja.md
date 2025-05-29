```
init_m0(sim::MicroSim, m0::TupleOrArrayOrFunction; norm=true)
```

システムの初期磁化を設定します。`norm=false`の場合、磁化配列は正規化されません。例:

```julia
   init_m0(sim, (1,1,1))
```

または

```julia
   init_m0(sim, (1,1,1), norm=false)
```

または

```julia
   function uniform_m0(i,j,k,dx,dy,dz)
       return (0,0,1)
   end
   init_m0(sim, uniform_m0)
```
