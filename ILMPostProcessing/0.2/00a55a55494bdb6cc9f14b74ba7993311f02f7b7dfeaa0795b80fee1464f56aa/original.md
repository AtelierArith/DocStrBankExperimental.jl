```
dmd(Xfull,r)
```

Compute the first `r` DMD modes from the extended snapshot data in `Xfull`. Both the original and shifted data are drawn from `Xfull`, that is: `X = Xfull[1:m-1]` and `Xp = Xfull[2:m]`

This returns the DMD modes and DMD eigenvalues in a `DMDModes` structure, with fields `modes` and `evals`.
