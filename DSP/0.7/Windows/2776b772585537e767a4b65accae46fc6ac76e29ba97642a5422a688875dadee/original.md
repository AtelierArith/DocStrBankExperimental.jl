```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │                                 ▄▀▀▚▖                                │ 
  │                              ▗▄▀    ▝▚▄                              │ 
  │                            ▗▞▘         ▀▄                            │ 
  │                          ▄▞▘             ▀▄▖                         │ 
  │                        ▄▀                  ▝▚▖                       │ 
  │                     ▗▄▀                      ▝▄▄                     │ 
  │                   ▗▞▘                           ▀▄                   │ 
  │                 ▄▞▘                               ▀▄▖                │ 
  │               ▄▀                                    ▝▚▖              │ 
  │            ▗▞▀                                        ▝▀▄            │ 
  │          ▗▞▘                                             ▀▄          │ 
  │        ▄▀▘                                                 ▀▚▖       │ 
  │      ▄▀                                                      ▝▚▖     │ 
  │   ▗▞▀                                                          ▝▀▄   │ 
0 │ ▄▞▘                                                               ▀▄▖│ 
  └──────────────────────────────────────────────────────────────────────┘ 
  0                                                                     70


bartlett(n::Integer; padding::Integer=0, zerophase::Bool=false)
bartlett(dims; padding=0, zerophase=false)
```

Bartlett window of length `n`. The Bartlett window is a triangular window that reaches 0 at the endpoints. This is equivalent to convolving two rectangular windows of length `(n-1)/2` and adding the zero endpoints. See `triang` for a window that does not reach zero at the endpoints.

The window is defined by sampling the continuous function:

```
1 - abs(2x)
```

in the range `[-0.5, 0.5]`

Providing a `dims` `Tuple` rather than a single `n` constructs a 2D window. `padding` and `zerophase` can then be given either as a single value for both horizontal and vertical or a 2-tuple to specify them separately.

If `zerophase` is `false` (the default) the window is centered around index `(n+1)/2`, which is commonly used for FIR filter design. These are often used for FIR filter design, and usually odd-length. Note that for even-length windows this will cause the window center to be located between samples.

If `zerophase` is `true` the window is centered around index 1 (with the negative half wrapped to the end of the vector). Additionally this creates a "periodic" window, which means that if there is no padding then the left and right endpoints of the window wrap around to the same sample, so the window length is the same as an `n+1`-length non-`zerophase` window. Alternatively you can think of the continuous `zerophase` window being of width `n` and the non-`zerophase` window being of length `n-1`. `zerophase` windows are often used in FFT processing, and are usually even-length.
