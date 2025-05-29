```
autoRmax(atom::Atom, n::Int; rmax=0.0)
```

Largest relevant radial distance in a.u. (rule of thumb value)

$$
    R_{max} = (2.5n^2 + 75.0)/Zc,
$$

where $n$ is the principal quantum number and $Z_c$ the Rydberg charge

#### Example:

```
julia> atom = castAtom(Z=1, A=1, Q=0);

julia> rmax = autoRmax(atom, n; rmax=0.0); println("rmax = $(rmax) a.u.")
rmax = 77.5 a.u.
```
