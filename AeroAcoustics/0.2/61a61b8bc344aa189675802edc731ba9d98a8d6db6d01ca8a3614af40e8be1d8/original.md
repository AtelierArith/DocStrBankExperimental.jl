```
csm(t;n=1024,noverlap=div(n,2),fs=1,win=DSP.hanning(n),scaling="spectrum")
```

Calculate cross-spectral matrix from time series `t` which is `S x M` dimensional, where `S` is the number of samples and `M`the number of microphones.
