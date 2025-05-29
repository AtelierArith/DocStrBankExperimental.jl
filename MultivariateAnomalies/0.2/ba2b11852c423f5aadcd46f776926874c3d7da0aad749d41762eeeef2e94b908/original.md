```
EWMA!(Z, dat,  λ)
```

use a preallocated output Z. `Z = similar(dat)` or `dat = dat` for overwriting itself.

# Examples

```
julia> dc = rand(100,3,2)
julia> EWMA!(dc, dc, 0.1)
```
