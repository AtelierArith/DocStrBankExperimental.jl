```
update_nobs!(nobs::NobsMatrixElement{T}; threshold = 1e-7)
```

This function makes sure that all the elements in `nobs` are synchronized. It should be called whenever the field `nobs.m` (matrix M_p in Eq. 10 of KurkiSuonio2009) has changed.
