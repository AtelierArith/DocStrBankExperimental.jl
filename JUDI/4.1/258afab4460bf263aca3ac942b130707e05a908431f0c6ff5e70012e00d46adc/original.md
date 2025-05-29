```
judiWavelet(dt, wavelet)
```

Low-rank wavefield operator which injects a wavelet q at every point of the subsurface.

# Examples

`F` is a modeling operator of type `judiModeling` and `w` is a weighting matrix of type `judiWeights`:     Pr = judiProjection(rec*geometry)     Pw = judiWavelet(rec*geometry.dt, q.data) # or judiLRWF(rec_geometry.dt, q.data)     dobs = Pr*F*Pw'*w     dw = Pw*F'*Pr'*dobs
