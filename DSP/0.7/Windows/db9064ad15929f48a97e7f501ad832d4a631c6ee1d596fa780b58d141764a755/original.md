```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │ ▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▘│ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
  │                                                                      │ 
0 │                                                                      │ 
  └──────────────────────────────────────────────────────────────────────┘ 
  0                                                                     70


rect(n::Integer; padding::Integer=0, zerophase::Bool=false)
rect(dims; padding=0, zerophase=false)
```

Rectangular window of length `n`, padded with `padding` zeros. This window is 1 within the window, and 0 outside of it.

Providing a `dims` `Tuple` rather than a single `n` constructs a 2D window. `padding` and `zerophase` can then be given either as a single value for both horizontal and vertical or a 2-tuple to specify them separately.

If `zerophase` is `false` (the default) the window is centered around index `(n+1)/2`, which is commonly used for FIR filter design. These are often used for FIR filter design, and usually odd-length. Note that for even-length windows this will cause the window center to be located between samples.

If `zerophase` is `true` the window is centered around index 1 (with the negative half wrapped to the end of the vector). Additionally this creates a "periodic" window, which means that if there is no padding then the left and right endpoints of the window wrap around to the same sample, so the window length is the same as an `n+1`-length non-`zerophase` window. Alternatively you can think of the continuous `zerophase` window being of width `n` and the non-`zerophase` window being of length `n-1`. `zerophase` windows are often used in FFT processing, and are usually even-length.
