```
  XFuzz, Ps1, Ps2 = XFuzzEn(Sig1, Sig2)
```

Returns the cross-fuzzy entropy estimates (`XFuzz`) and the average fuzzy   distances (m:Ps1, m+1:Ps2) for m = [1,2] estimated for the data sequences   contained in `Sig1` and `Sig2`, using the default parameters: embedding dimension = 2,   time delay = 1, fuzzy function (Fx) = 'default',    fuzzy function parameters (r) = [0.2, 2], logarithm = natural

```
  XFuzz, Ps1, Ps2 = XFuzzEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Tuple{Real,Real}}=(.2,2), Fx::String="default", Logx::Real=exp(1))
```

Returns the cross-fuzzy entropy estimates (`XFuzz`) for dimensions = [1,...,m]   estimated for the data sequences in `Sig1` and `Sig2` using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer   [default: 2]    

`tau`   - Time Delay, a positive integer            [default: 1]    

`Fx`    - Fuzzy function name, one of the following:              {`"sigmoid", "modsampen", "default", "gudermannian",`             `"bell", "triangular", "trapezoidal1", "trapezoidal2",`             `"z_shaped", "gaussian", "constgaussian"`}

`r`     - Fuzzy function parameters, a scalar or a 2 element tuple              of positive values. The `r` parameters for each fuzzy             function are defined as follows:

```
        sigmoid:        r(1) = divisor of the exponential argument
                        r(2) = value subtracted from argument (pre-division)
        modsampen:      r(1) = divisor of the exponential argument
                        r(2) = value subtracted from argument (pre-division)
        default:        r(1) = divisor of the exponential argument
                        r(2) = argument exponent (pre-division)
        gudermannian:   r    = a scalar whose value is the numerator of
                              argument to gudermannian function:
                              GD(x) = atan(tanh(`r`/x)).
        triangular:     r = a scalar whose value is the threshold (corner point) of the triangular function.
        trapezoidal1:   r = a scalar whose value corresponds to the upper (2r) and lower (r) corner points of the trapezoid.
        trapezoidal2:   r(1) = a value corresponding to the upper corner point of the trapezoid.
                        r(2) = a value corresponding to the lower corner point of the trapezoid.
        z_shaped:       r = a scalar whose value corresponds to the upper (2r) and lower (r) corner points of the z-shape.
        bell:           r(1) = divisor of the distance value
                        r(2) = exponent of generalized bell-shaped function
        gaussian:       r = a scalar whose value scales the slope of the Gaussian curve.
        constgaussian:  r = a scalar whose value defines the lower threshod and shape of the Gaussian curve.                    
        [DEPRICATED] linear:       r  = an integer value. When r = 0, the
                              argument of the exponential function is 
                              normalised between [0 1]. When r = 1,
                              the minimuum value of the exponential 
                              argument is set to 0.
```

`Logx`  - Logarithm base, a positive scalar  

For further information on the 'keyword' arguments, see the EntropyHub guide.

# See also `FuzzEn`, `XSampEn`, `XApEn`, `FuzzEn2D`, `XMSEn`, `MSEn`

# References:

```
  [1] Hong-Bo Xie, et al.,
      "Cross-fuzzy entropy: A new method to test pattern synchrony of
      bivariate time series." 
      Information Sciences 
      180.9 (2010): 1715-1724.

  [3] Hamed Azami, et al.
      "Fuzzy Entropy Metrics for the Analysis of Biomedical Signals: 
      Assessment and Comparison"
      IEEE Access
      7 (2019): 104833-104847
```
