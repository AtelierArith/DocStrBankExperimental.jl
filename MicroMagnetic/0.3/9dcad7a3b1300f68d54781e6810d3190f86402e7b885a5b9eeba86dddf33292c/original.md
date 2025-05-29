```
update_zeeman(sim::AbstractSim, H0::TupleOrArrayOrFunction; name="zeeman")
```

Set the Zeeman field to H0 where H0 is TupleOrArrayOrFunction according to its name. For example,

```julia
   add_zeeman(sim, (0,0,0), name="my_H")  #create a zeeman energy with field (0,0,0) A/m
   update_zeeman(sim, (0,0,1e5), name="my_H")  #change the field to (0,0,1e5) A/m
```
