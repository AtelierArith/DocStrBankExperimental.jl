```
SeisRadonFreqInv(d; <keyword arguments>)
```

Transform a Gather from time-offset gather to tau-p gather using a frequency domain inverse parabolic or linear Radon operator via least-squares inversion.

# Arguments

  * `d::Array{Float64,2}`: 2D data, `d[1:nt,1:nh]`, where `nt` is number of

time samples and `nh` the number of receivers.

# Keyword arguments

  * `order::"parab"`: `"parab"` for parabolic transform, `"linear"`

for linear transform.

  * `dt=0.004`: sampling interval in seconds.
  * `h=collect(0.0:20.0:1000.0)`: offset vector `h[1:nh]`.
  * `href=0.0`: reference offset for parabolic Radon Transform. If the

defautl value `href=0.0` is given, `href` is set to `max(abs(h))`.

  * `p=collect(-0.05:0.01:2.2)`: `p[1:np]`. If `order="parab"`, `p`

is a vector of residual moveout ("curvatures") at reference offset `href` in seconds; if `order=linear`, `p` is a vector of ray parameters in s/m.

  * `flow=0.0`: minimum frequency in the data in Hz.
  * `fhigh=125.0`: maximum frequency in the data in Hz.
  * `mu=0.001`: trade off parameter or damping for the L.S. inversion.

# Output

  * `m`: inverted Radon panel `m[1:ntau, 1:np]`.

# References

  * Hampson, D., 1986, Inverse velocity stacking for multiple elimination:

Canadian Journal of Exploration Geophysics, 22, 44-55.

  * Sacchi, M.D. and Ulrych, T.J., 1995, High-resolution velocity gathers and

offset space reconstruction: Geophysics, 60, 1169-1177.
