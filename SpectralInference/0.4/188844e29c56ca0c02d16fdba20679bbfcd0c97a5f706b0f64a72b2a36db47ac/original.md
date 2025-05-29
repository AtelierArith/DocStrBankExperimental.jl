```
projectout(usv::SVD, [window])
```

recreates original matrix i.e. calculates $UΣV'$ or if window is included  creates a spectrally filtered version of the original matrix off of the provided components in `window`.

i.e., `usv.U[:, window] * diagm(usv.S[window]) * usv.Vt[window, :]`
