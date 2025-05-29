```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │                                ▄▞▀▀▀▄▖                               │ 
  │                            ▗▄▞▀      ▝▀▄▖                            │ 
  │                         ▗▄▀▘            ▝▀▄▖                         │ 
  │                      ▗▄▀▘                  ▝▀▄▖                      │ 
  │                   ▗▄▀▘                        ▝▀▄▖                   │ 
  │                ▗▄▀▘                              ▝▀▄▄                │ 
  │             ▗▄▀▘                                     ▀▚▄             │ 
  │          ▗▄▀▘                                           ▀▙▄          │ 
  │       ▄▄▀▘                                                 ▀▚▄       │ 
  │    ▄▞▀                                                        ▀▚▄    │ 
  │ ▄▞▀                                                              ▀▚▄ │ 
  │▀                                                                    ▀│ 
  │                                                                      │ 
  │                                                                      │ 
0 │                                                                      │ 
  └──────────────────────────────────────────────────────────────────────┘ 
  1                                                                      7


triang(n::Integer; padding::Integer=0, zerophase::Bool=false)
triang(dims; padding=0, zerophase=false)
```

Triangular window of length `n` with `padding` zeros. The Triangular window does not reach zero at the endpoints. For odd `n` the `triang` window is the center `n` points of an `n+2`-point [`bartlett`](@ref) window (i.e. the samples just outside the window would be zero). For even `n` the window slope is the same as the `n-1` window but delayed by a half sample so the zero points would be 1/2 sample past the ends of the window.

The window is defined by sampling the continuous function:

```
        ⎛    2(n-1)
        ⎜1 - ────── abs(x)     n is even
        ⎜       n
w(x) =  ⎜
        ⎜    2(n-1)
        ⎜1 - ────── abs(x)     n is odd
        ⎝     n+1
```

in the range `[-0.5, 0.5]`.

Providing a `dims` `Tuple` rather than a single `n` constructs a 2D window. `padding` and `zerophase` can then be given either as a single value for both horizontal and vertical or a 2-tuple to specify them separately.

If `zerophase` is `false` (the default) the window is centered around index `(n+1)/2`, which is commonly used for FIR filter design. These are often used for FIR filter design, and usually odd-length. Note that for even-length windows this will cause the window center to be located between samples.

If `zerophase` is `true` the window is centered around index 1 (with the negative half wrapped to the end of the vector). Additionally this creates a "periodic" window, which means that if there is no padding then the left and right endpoints of the window wrap around to the same sample, so the window length is the same as an `n+1`-length non-`zerophase` window. Alternatively you can think of the continuous `zerophase` window being of width `n` and the non-`zerophase` window being of length `n-1`. `zerophase` windows are often used in FFT processing, and are usually even-length.

When `zerophase` is `true` substitute `n+1` for `n` in the above window expressions.
