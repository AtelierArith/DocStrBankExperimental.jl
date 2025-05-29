```
SeisMWNI(in;<keyword arguments>)
```

Minimum Weighted Norm Interpolation of seismic records.

# Arguments

  * `in`: up to 5D input data. First dimension is time.
  * `dt=0.001` : sampling rate along the time axis (in seconds)
  * `fmax=99999.` : maximum temporal frequency to process.
  * `padt=2` : padding in the time axis, first dimension.
  * `padx=1` : padding in the spatial axes. (Dim 2 to 5).
  * `Niter_internal=10` : number of internal iterations for Conjugate Gradients
  * `Niter_external=3` : number of external iterations for iterative reweighting
  * `mu=0`
