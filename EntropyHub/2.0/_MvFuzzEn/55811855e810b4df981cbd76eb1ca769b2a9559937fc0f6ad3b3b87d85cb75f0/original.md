```
MFuzz, B0, Bt, B1 = MvFuzzEn(Data)
```

Returns the multivariate fuzzy entropy estimate (`MFuzz`) and the   average vector distances (`m`: `B0`; joint total `m+1` subspace: `Bt`;   all possible `m+1` subspaces: `B1`), from the M multivariate sequences  in `Data` using the default parameters:   embedding dimension = 2*ones(M,1), time delay = ones(M,1),   fuzzy membership function = "default", fuzzy function parameters= [0.2, 2],  logarithm = natural, data normalization = false,

!!! note
    The entropy value returned as `MFuzz` is estimated using the "full"  method [i.e.  -log(Bt/B0)] which compares delay vectors across all possible `m+1`  expansions of the embedding space as applied in [1][3]. Contrary to conventional definitions of sample entropy, this method does not provide a lower bound of 0!! Thus, it is possible to obtain negative entropy values for multivariate  fuzzy entropy, even for stochastic processes...

    Alternatively, one can calculate `MFuzz` via the "naive" method,  which ensures a lower bound of 0, by using the average vector distances for an individual `m+1` subspace (B1) [e.g. -log(B1(1)/B0)], or the average for all `m+1` subspaces [i.e. -log(mean(B1)/B0)].

    To maximize the number of points in the embedding process, this algorithm  uses N - max(m * tau) delay vectors and **not** N - max(m) * max(tau) as employed  in [1] and [3].


---

```
MFuzz, B0, Bt, B1 = MvFuzzEn(Data::AbstractArray{T} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, r::Union{Real,Tuple{Real,Real}}=(.2,2.0), Fx::String="default", Logx::Real=exp(1), Norm::Bool=false)
```

Returns the multivariate sample entropy estimates (`MSamp`) estimated  from the M multivariate data sequences in `Data` using the specified   keyword arguments:

# Arguments:

`Data`  - Multivariate dataset, NxM matrix of N (>10) observations (rows) and M (cols) univariate data sequences

`m`     - Embedding Dimension, a vector of M positive integers

`tau`   - Time Delay, a vector of M positive integers

`Fx`    - Fuzzy function name, one of the following:              {`"sigmoid", "modsampen", "default", "gudermannian",`             `"bell", "triangular", "trapezoidal1", "trapezoidal2",`             `"z_shaped", "gaussian", "constgaussian"`}

`r`      - Fuzzy function parameters, a 1 element scalar or a 2 element                 tuple of positive values. The `r` parameters for each fuzzy                 function are defined as follows:      [default: [.2 2]]

```
            default:        r(1) = divisor of the exponential argument
                            r(2) = argument exponent (pre-division)
            sigmoid:        r(1) = divisor of the exponential argument
                            r(2) = value subtracted from argument (pre-division)
            modsampen:      r(1) = divisor of the exponential argument
                            r(2) = value subtracted from argument (pre-division)
            gudermannian:   r  = a scalar whose value is the numerator of
                                argument to gudermannian function:
                                GD(x) = atan(tanh(`r`/x))
            triangular:     r = a scalar whose value is the threshold (corner point) of the triangular function.
            trapezoidal1:   r = a scalar whose value corresponds to the upper (2r) and lower (r) corner points of the trapezoid.
            trapezoidal2:   r(1) = a value corresponding to the upper corner point of the trapezoid.
                            r(2) = a value corresponding to the lower corner point of the trapezoid.
            z_shaped:       r = a scalar whose value corresponds to the upper (2r) and lower (r) corner points of the z-shape.
            bell:           r(1) = divisor of the distance value
                            r(2) = exponent of generalized bell-shaped function
            gaussian:       r = a scalar whose value scales the slope of the Gaussian curve.
            constgaussian:  r = a scalar whose value defines the lower threshod and shape of the Gaussian curve.
```

`Logx`   - Logarithm base, a positive scalar 

`Norm`   - Normalisation of all M sequences to unit variance, a boolean

# See also `MvSampEn`, `FuzzEn`, `XFuzzEn`, `FuzzEn2D`, `MSEn`, `MvPermEn`

# References:

```
[1] Ahmed, Mosabber U., et al. 
    "A multivariate multiscale fuzzy entropy algorithm with application
    to uterine EMG complexity analysis." 
    Entropy 19.1 (2016): 2.

[2] Azami, Alberto Fernández, Javier Escudero. 
    "Refined multiscale fuzzy entropy based on standard deviation for 
    biomedical signal analysis." 
    Medical & biological engineering & computing 55 (2017): 2037-2052.

[3] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy analysis."
    IEEE signal processing letters 19.2 (2011): 91-94.
```
