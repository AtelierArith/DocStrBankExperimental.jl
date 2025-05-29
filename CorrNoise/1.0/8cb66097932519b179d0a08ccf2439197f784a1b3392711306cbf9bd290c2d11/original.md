```
initflatrng128(xstart = 123456789, ystart = 362436069, zstart = 521288629, wstart = 88675123)
```

Initialize a flat random number generator with period 2^128. To draw random numbers, use the `Base.rand` function as usual.

Example:

```
rng = initflatrng128()
print([rand(rng) for i in 1:4])
```
