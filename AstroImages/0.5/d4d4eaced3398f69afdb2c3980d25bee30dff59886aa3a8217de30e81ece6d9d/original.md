```
Zscale(options)(data)
```

Wraps PlotUtils.zscale in a callable with default parameters. This is a common algorithm for agressively stretching astronomical data to see faint structure that originated in IRAF: [https://iraf.net/forum/viewtopic.php?showtopic=134139](https://iraf.net/forum/viewtopic.php?showtopic=134139) but is now seen in many other applications/libraries (DS9, Astropy, etc.)

Usage:

```julia
imview(img, clims=Zscale())
implot(img, clims=Zscale(contrast=0.1))
```

Default parameters:

```
nsamples::Int=1000
contrast::Float64=0.25
max_reject::Float64=0.5
min_npixels::Float64=5
k_rej::Float64=2.5
max_iterations::Int=5
```
