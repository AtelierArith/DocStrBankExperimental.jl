```
NonlinearNormalForm.TPSAMap(m::Union{TaylorMap{S,T,U,V,W},Probe{S,T,U,V,W}}; use::UseType=m, idpt::Union{Nothing,Bool}=m.idpt) where {S,T,U,V,W}
```

Creates a new copy of the passed `TaylorMap` as a `NonlinearNormalForm.TPSAMap`. 

If `use` is not specified, then the same GTPSA `Descriptor` as `m` will be used. If `use` is  specified (could be another `Descriptor`, `TaylorMap`, or a `Probe` containing `TPS`s), then the  copy of `m` as a new NonlinearNormalForm.TPSAMap will have the same `Descriptor` as in `use.` The total number of variables +  parameters must agree, however the orders may be different.

If `idpt` is not specified, then the same `idpt` as `m` will be used, else that specified will be used.
