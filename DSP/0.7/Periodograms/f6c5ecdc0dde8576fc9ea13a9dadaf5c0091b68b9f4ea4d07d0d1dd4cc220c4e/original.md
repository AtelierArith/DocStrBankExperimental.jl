```
periodogram(s::AbstractMatrix; nfft=nextfastfft(size(s)), fs=1, radialsum=false, radialavg=false)
```

Computes periodogram of a 2-d signal by FFT and returns a Periodogram2 object.

Returns a 2-d periodogram by default. A radially summed or averaged periodogram is returned as a Periodogram object if `radialsum` or  `radialavg` is true, respectively.

`nfft` specifies the number of points to use for the Fourier transform. If `size(s)` < `nfft`, then the input is padded with zeros. By default, `nfft` is the closest size for which the Fourier transform can be computed with maximal efficiency. `fs` is the sample rate of the original signal in both directions.

For `radialsum=true` the value of `power[k]` is proportional to $\frac{1}{N}\sum_{k\leq |k'|<k+1} |X[k']|^2$. For `radialavg=true` it is proportional to $\frac{1}{N \#\{k\leq |k'|<k+1\}} \sum_{k\leq |k'|<k+1} |X[k']|^2$. The computation of `|k'|` takes into account non-square signals by scaling the coordinates of the wavevector accordingly.
