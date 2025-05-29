```
subfields(C::ClassField; degree::Int, is_normal, type) -> Vector{ClassField}
```

Find all subfields of $C$ over the base field.

If the optional keyword argument `degree` is positive, then only those with prescribed degree will be returned.

If the optional keyword `is_normal` is given, then only those that are normal over the field fixed by the automorphisms is returned. For normal base fields, this amounts to extensions that are normal over `Q`.

If the optional keyword `is_normal` is set to a list of automorphisms, then only those wil be considered.

`type` can be set to the desired relative Galois group, given as a vector of integers descibing the structure.

!!! note
    This will not find all subfields over $\mathbf{Q}$, but only the ones sharing the same base field.

