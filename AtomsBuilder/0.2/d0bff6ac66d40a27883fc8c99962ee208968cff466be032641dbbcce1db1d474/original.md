`randz!(sys::FlexibleSystem, zlist) -> sys`

Randomly assigns elements to the atoms in the system `sys` according to the probabilities given in `zlist`. `zlist` is an iterable over pairs of the form `id => p` where `id` is an atom id (e.g. atomic number or chemical symbol) and `p`  a probability. E.g., 

```
sys = bulk(:Ti, cubic=true) * 3
sys = randz!(sys, [ :Ti => 0.2, :O => 0.8 ])
```

This function was developed mostly for generating testing  systems. It may not be suitable for generating random alloys.  PRs to improve it are welcome. 
