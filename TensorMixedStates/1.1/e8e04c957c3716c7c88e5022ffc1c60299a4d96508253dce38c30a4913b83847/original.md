```
@def_operators(site, symbols, fermionic=false)
```

define the given operator for the given site

# Examples

```
@def_operators(Fermion(),
[
    C = [0. 1. ; 0. 0.],
],
true)

@def_operators(Fermion(),
[
    F = [1. 0. ; 0. -1.],
    A = C,
    N = dag(C)*C
])
```
