```
 pm2pa(At::PeriodicMatrix) -> A::PeriodicArray
```

Convert a discrete-time periodic matrix object into a discrete-time periodic array object.

The discrete-time periodic matrix object `At` contains a   `p`-vector `At` of real matrices `At[i]`, `i = 1,..., p`,  the associated time period `T` and the number of subperiods `k`. The resulting discrete-time periodic array object `A` of period `T` and number of subperiods `k`  is built from a `m×n×p` real array `A`, such that `A[:,:,i]`  contains `At[i]`, for `i = 1,..., p`.  For non-constant dimensions, the resulting `m` and `n` are the maximum row and column dimensions, respectively, and the resulting component matrices `A[:,:,i]` contain `At[i]`, appropriately padded with zero entries. 
