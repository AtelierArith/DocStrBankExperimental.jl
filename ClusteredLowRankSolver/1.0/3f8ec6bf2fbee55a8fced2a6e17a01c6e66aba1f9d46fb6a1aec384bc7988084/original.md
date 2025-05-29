```
find_field(primalsol, dualsol, max_degree=4; valbound=1e-15, errbound=1e-15, bits=100, max_coeff=1000)
```

Heuristically find a field over which the kernel can probably be defined. 

Only consider values at least `valbound` in absolute value. Find minimal polynomials  such that the chosen entries are approximately generators with an error bound of `errbound`. Use `bits` number of bits and reject minimal polynomials with a maximum coefficient of more than `max_coeff`.
