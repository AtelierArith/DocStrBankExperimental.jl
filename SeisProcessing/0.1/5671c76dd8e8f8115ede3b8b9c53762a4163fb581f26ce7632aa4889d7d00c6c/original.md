```
SeisRadonFreqFor(in, nt; <keyword arguments>)
```

Transform a tau-p gather to a time-offset gather using a frequency domain forward parabolic or linear Radon operator.

# Arguments

  * `in::Array{Float64,2}`: 2D Radon panel, `in[1:ntau,1:np]`, where `ntau` is the

number of intercept times and `np` the number of curvatures or ray parameters.

  * `nt::Int`: number of time samples.

# Keyword arguments

  * `order="parab"`: `"parab"` for parabolic transform, `"linear"`

for linear transform.

  * `dt=0.004`: time sampling interval in seconds.
  * `h=collect(0.0:20.0:1000.0)`: offset vector; `h[1:nh]`.
  * `href=0.0`: reference offset for parabolic Radon Transform. If the

defautl value `href=0.0` is given, `href` is set to `max(abs(h))`.

  * `p=collect(-0.05:0.01:2.2)`: `p[1:np]`. If `order="parab"`, `p`

is a vector of residual moveout ("curvatures") at reference offset `href` in seconds; if `order=linear`, `p` is a vector of ray parameters in s/m.

  * `flow=0.0`: minimum frequency in the data in Hz.
  * `fhigh=125.0`: maximum frequency in the data in Hz.

# Output

  * `d`: data synthetized via forward Radon modeling, `d[1:nt, 1:nh]`.

# References

  * Hampson, D., 1986, Inverse velocity stacking for multiple elimination:

Canadian Journal of Exploration Geophysics, 22, 44-55.

  * Sacchi, M.D. and Ulrych, T.J., 1995, High-resolution velocity gathers and

offset space reconstruction: Geophysics, 60, 1169-1177.
