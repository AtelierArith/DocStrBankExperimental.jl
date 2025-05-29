```
`bind!(dest, src, twoway=true; initial=true)`
```

for every update to `src` also update `dest` with the same value and, if `twoway` is true, vice-versa. If `initial` is false, `dest` will only be updated to `src`'s value when `src` next updates, otherwise (if `initial` is true) both `dest` and `src` will take `src`'s value immediately.
