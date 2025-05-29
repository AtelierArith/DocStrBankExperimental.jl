```
  ┌──────────────────────────────────────────────────────────────────────┐ 
1 │                             ▗▄▞▀▀▀▀▀▀▀▄▄                             │ 
  │                           ▄▞▘           ▀▄▖                          │ 
  │                         ▄▀                ▝▚▖                        │ 
  │                       ▗▞                    ▝▄                       │ 
  │                      ▞▘                      ▝▚▖                     │ 
  │                    ▗▀                          ▝▚                    │ 
  │                   ▞▘                             ▀▖                  │ 
  │                 ▗▞                                ▝▄                 │ 
  │                ▄▘                                   ▚▖               │ 
  │              ▗▞                                      ▝▄              │ 
  │             ▄▘                                         ▚▖            │ 
  │           ▗▀                                            ▝▚           │ 
  │         ▗▞▘                                               ▀▄         │ 
  │       ▄▀▘                                                   ▀▚▖      │ 
0 │ ▄▄▄▄▀▀                                                        ▝▀▚▄▄▄▖│ 
  └──────────────────────────────────────────────────────────────────────┘ 
  0                                                                     70


hanning(n::Integer; padding::Integer=0, zerophase::Bool=false)
hanning(dims; padding=0, zerophase=false)
```

Hanning window of length `n` with `padding` zeros. The Hanning (or Hann) window is a raised-cosine window that reaches zero at the endpoints.

The window is defined by sampling the continuous function:

```
       1 + cos(2πx)
w(x) = ──────────── = cos²(πx)
            2
```

in the range `[-0.5, 0.5]`

The `hanning` window satisfies the Constant Overlap-Add (COLA) property with an hop of 0.5, which means that adding together a sequence of delayed windows with 50% overlap will result in a constant signal. This is useful when synthesizing a signal from a number of overlapping frames (each with a roughly rectangular window), to eliminate windowing amplitude modulation.

Note that the `hanning` window is the `cosine` window squared.

Providing a `dims` `Tuple` rather than a single `n` constructs a 2D window. `padding` and `zerophase` can then be given either as a single value for both horizontal and vertical or a 2-tuple to specify them separately.

If `zerophase` is `false` (the default) the window is centered around index `(n+1)/2`, which is commonly used for FIR filter design. These are often used for FIR filter design, and usually odd-length. Note that for even-length windows this will cause the window center to be located between samples.

If `zerophase` is `true` the window is centered around index 1 (with the negative half wrapped to the end of the vector). Additionally this creates a "periodic" window, which means that if there is no padding then the left and right endpoints of the window wrap around to the same sample, so the window length is the same as an `n+1`-length non-`zerophase` window. Alternatively you can think of the continuous `zerophase` window being of width `n` and the non-`zerophase` window being of length `n-1`. `zerophase` windows are often used in FFT processing, and are usually even-length.
