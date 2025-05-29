```
fock_to_cart(addr, S; zero_index = true)
```

Convert a Fock state address `addr` to Cartesian harmonic oscillator basis indices $n_x,n_y,\ldots$. These indices are bounded by `S` which is a tuple of the maximum number of states in each dimension. By default the groundstate in each dimension is indexed by `0`, but this can be changed by setting `zero_index = false`.
