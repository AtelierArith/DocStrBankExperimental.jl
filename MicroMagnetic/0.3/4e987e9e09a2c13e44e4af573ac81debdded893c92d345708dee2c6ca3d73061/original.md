```
init_m0(sim::MicroSim, m0::TupleOrArrayOrFunction; norm=true)
```

Set the initial magnetization of the system. If `norm=false` the magnetization array will be not normalised. Examples:

```julia
   init_m0(sim, (1,1,1))
```

or

```julia
   init_m0(sim, (1,1,1), norm=false)
```

or

```julia
   function uniform_m0(i,j,k,dx,dy,dz)
       return (0,0,1)
   end
   init_m0(sim, uniform_m0)
```
