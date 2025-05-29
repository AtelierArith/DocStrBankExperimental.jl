```
SeisPOCS(in;<keyword arguments>)
```

Projection Onto Convex Sets interpolation of seismic records.

# Arguments

  * `in`: input data that can have up to 5 dimensions. Time is in the first dimension.
  * `p=1.` : exponent for thresholding (1 is equivalent to soft thres. high number is equivalent to hard thresholding)
  * `alpha=1` : add-back ratio for imputation step. Use 1 for noise free data, and < 1 for denoising of original traces.
  * `dt=0.001` : sampling rate along the time axis (in seconds)
  * `fmax=99999.` : maximum temporal frequency to process.
  * `padt=2` : padding in the time axis, first dimension.
  * `padx=1` : padding in the spatial axes. (Dim 2 to 5).
  * `Niter=100` : number of iterations
  * `alpha=1`
