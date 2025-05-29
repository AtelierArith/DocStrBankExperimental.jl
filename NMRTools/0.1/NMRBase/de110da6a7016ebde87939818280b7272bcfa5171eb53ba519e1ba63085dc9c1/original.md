```
GaussWindow(expHz, gaussHz, center, tmax)
```

Abstract representation of Lorentz-to-Gauss window functions, applying an inverse exponential of `expHz` Hz, and a gaussian broadening of `gaussHz` Hz, with maximum at `center` (between 0 and 1). Acquisition time is `tmax`.

Specialises to `LorentzToGaussWindow` when `center` is zero, otherwise `GeneralGaussWindow`.
