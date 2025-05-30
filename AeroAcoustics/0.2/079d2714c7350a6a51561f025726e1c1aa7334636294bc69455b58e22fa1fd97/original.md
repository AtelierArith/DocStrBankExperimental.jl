```
cleanSC(E[;maxiter=50,ϕ=0.5,stopn=10,peak_removal=false,trust_region=nothing])
```

CLEAN-SC algorithm for source identification and quantification optionally setting maximum iterations `maxiter` (default 50), and loop gain `ϕ` (default 0.5). Additionally, a stopping criterion `max_peak[i] > max_peak[i-stopn]` can be set with parameter `stopn`. Subtraction of peak sources in the dirty map is supported by `peak_removal=true/false` to remove peak sources outside `trust_region` with limits given as `[xmin,xmax,ymin,ymax]` e.g. `trust_region=[-0.75;1.5;-1.0;1.0]`.

# References:

-	Sijtsma, P. (2007). CLEAN based on spatial source coherence. International Journal of Aeroacoustics, 6(4), 357–374.

With inspiration from https://github.com/acoular/acoular/blob/66cba3cffb3bc72602c869f99347be76798f4ac1/acoular/fbeamform.py#L1496
