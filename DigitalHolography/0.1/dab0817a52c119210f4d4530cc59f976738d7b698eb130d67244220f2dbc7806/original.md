```
GeneralizedPSDH(I)
```

return object wave extracted by the generalized phase-shifting method. See (Creath, 1988), (Schreiber and Bruning, 2006). Store N interferograms in a three-dimensional array as `I[:,:,1]`, `I[:,:,2]`, ..., `I[:,:,N]`. Phase difference $\delta_{n}$ corresponding to the n-th interferogram is assumed to be $\delta_{n} = \dfrac{2\pi}{N}n$.
