`rootdatum(C::AbstractMatrix)`  adjoint root datum  from Cartan matrix `C`. It  is the  same as  `rootdatum(one(C),C)`. The  adjoint group  is also the default  returned for `coxeter_group(type,rank)`. The following methods all define `pgl₃`.

```julia-repl
julia> rootdatum(cartan(:A,3))==coxgroup(:A,3)
true

julia> rootdatum(:pgl,3)
pgl₃
```
