```
@def_operators(site, symbols, fermionic=false)
```

指定されたサイトのために与えられた演算子を定義します

# 例

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
