```
bohrformula(Z::Int, n::Int)
```

Hydrogenic energy (in Hartree a.u.) for *atom* with *atomic number* `Z` and *principal quantum number* `n`.

$$
    E_n = - \frac{Z^2}{2n^2}
$$

#### Example:

```
julia> Z = 2; n = 4;

julia> bohrformula(Z,n)
-1//8
```
