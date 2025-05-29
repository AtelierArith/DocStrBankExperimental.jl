```
sweep!(A, k ; inv=false)
sweep!(A, ks; inv=false)
```

Perform the sweep operation (or inverse sweep if `inv=true`) on matrix `A` on element `k` (or each element in `ks`).  Only the upper triangle is read/swept.

# Example:

```
x = randn(100, 10)
xtx = x'x
sweep!(xtx, 1)
sweep!(xtx, 1, true)
```
