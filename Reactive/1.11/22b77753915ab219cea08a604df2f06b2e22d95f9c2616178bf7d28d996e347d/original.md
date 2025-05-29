```
`bindmap!(dest::Signal, src2dest::Function, src::Signal, dest2src=nothing; initial=true)`
```

for every update to `src` also update `dest` with a modified value (using the function `src2dest`) and, if `dest2src` is specified, a two-way update will hold. If `initial` is false, `dest` will only be updated to `src`'s modified value when `src` next updates, otherwise (if `initial` is true) both `dest` and `src` will take their respective modified values immediately.
