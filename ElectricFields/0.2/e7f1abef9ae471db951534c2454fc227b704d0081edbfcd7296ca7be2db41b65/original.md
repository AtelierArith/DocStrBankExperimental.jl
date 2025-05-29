```
steps(f[, fs])
```

Return number of time steps for the field `f`, optionally supplying a sampling frequency.

We construct the time axis such that the highest frequency component of the field is resolved. By the Nyquist sampling theorem, we need minimum $f_s>2f_{\textrm{max}}$, but to be on the safe side, we use, as default, $f_s=100f_{\textrm{max}}$. This also makes plots nicer.

If `fs<:Integer`, the sampling frequency is computed as `fs/T`, i.e. `fs` steps per cycle.
