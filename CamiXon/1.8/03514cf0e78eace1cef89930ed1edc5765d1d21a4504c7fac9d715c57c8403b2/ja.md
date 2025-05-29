```
bohrformula(Z::Int, n::Int)
```

水素様エネルギー（Hartree a.u.単位）を*原子*の*原子番号* `Z` と*主量子数* `n` に対して計算します。

$$
    E_n = - \frac{Z^2}{2n^2}
$$

#### 例:

```
julia> Z = 2; n = 4;

julia> bohrformula(Z,n)
-1//8
```
