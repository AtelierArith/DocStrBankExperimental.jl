```
autoRmax(atom::Atom, n::Int; rmax=0.0)
```

原子単位での最も関連する最大半径距離（経験則値）

$$
    R_{max} = (2.5n^2 + 75.0)/Zc,
$$

ここで、$n$は主量子数、$Z_c$はリュードベリ電荷です。

#### 例:

```
julia> atom = castAtom(Z=1, A=1, Q=0);

julia> rmax = autoRmax(atom, n; rmax=0.0); println("rmax = $(rmax) a.u.")
rmax = 77.5 a.u.
```
