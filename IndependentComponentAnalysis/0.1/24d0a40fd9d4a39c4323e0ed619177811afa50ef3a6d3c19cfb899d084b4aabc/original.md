```
est, H = duet( x1, x2, n_sources, n = 1024;
    p            = 1, # amplitude power used to weight histogram
    q            = 0, # delay power used to weight histogram
    amax         = 0.7,
    dmax         = 3.6,
    abins        = 35, # number of histogram bins
    dbins        = 50, # number of histogram bins
    kernel_size  = 1, # Controls the smoothing of the histogram.
    window       = hanning,
    bigdelay     = false,
    kernel_sizeδ = 0.1,
    kwargs..., # These are sent to the stft function
)
```

DUET is an algorithm for blind source separation. It works on stereo mixtures and can separate any number of sources as long as they do not overlap in the time-frequency domain.

## `p` and `q`

The paper gives the following guidelines:

  * `p = 0, q = 0`: the counting histogram proposed in the original DUET algorithm
  * `p = 1, q = 0`: motivated by the ML symmetric attenuation estimator
  * `p = 1, q = 2`: motivated by the ML delay estimator
  * `p = 2, q = 0`: in order to reduce delay estimator bias
  * `p = 2, q = 2`: for low signal-to-noise ratio or speech mixtures

From the paper referenced below: "`p = 1, q = 0` is a good default choice. When the sources are not equal power, we would suggest `p = 0.5, q = 0` as it prevents the dominant source from hiding the smaller source peaks in the histogram."

For large delays, it appears to be more efficient to set `dmax` to something small (20), `nfft ≈ 8n, p=0.5, q=2`

  * `bigdelay` indicates whether or not the two microphones are far apart. If `true`, the delay `δ` is estimated using the differential method (see the paper sec 8.4.1) and the delay map is smoothed using `kernel_sizeδ`.

Implementation based on *Rickard, Scott. (2007). The DUET blind source separation algorithm. 10.1007/978-1-4020-6479-1_8.*
