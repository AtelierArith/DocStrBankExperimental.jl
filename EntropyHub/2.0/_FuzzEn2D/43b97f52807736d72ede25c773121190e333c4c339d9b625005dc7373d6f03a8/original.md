```
Fuzz2D = FuzzEn2D(Mat)
```

Returns the bidimensional fuzzy entropy estimate (`Fuzz2D`) estimated for  the data matrix (`Mat`) using the default parameters: time delay = 1, fuzzy function (Fx) = 'default', fuzzy function parameters (r) = [0.2, 2], logarithm = natural, template matrix size = [floor(H/10) floor(W/10)],  (where H and W represent the height and width of the data matrix 'Mat') 

** The minimum dimension size of Mat must be > 10.**

```
Fuzz2D = FuzzEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10), 
                    tau::Int=1, r::Union{Real,Tuple{Real,Real}}=(.2*std(Mat, corrected=false),2), 
                        Fx::String="default", Logx::Real=exp(1), Lock::Bool=true)
```

Returns the bidimensional fuzzy entropy (`Fuzz2D`) estimates for the data matrix (`Mat`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Template submatrix dimensions, an integer scalar (i.e. the same           height and width) or a two-element vector of integers            [height, width] with a minimum value > 1.           (default: [floor(H/10) floor(W/10)])  

`tau`   - Time Delay, a positive integer   (default: 1)  

`Fx`    - Fuzzy function name, one of the following:            {`"sigmoid", "modsampen", "default", "gudermannian",`           `"bell", "triangular", "trapezoidal1", "trapezoidal2",`           `"z_shaped", "gaussian", "constgaussian"`}

`r`     - Fuzzy function parameters, a 1 element scalar or a 2 element           vector of positive values. The 'r' parameters for each fuzzy           function are defined as follows:

```
      sigmoid:        r(1) = divisor of the exponential argument
                      r(2) = value subtracted from argument (pre-division)
      modsampen:      r(1) = divisor of the exponential argument
                      r(2) = value subtracted from argument (pre-division)
      default:        r (1) = divisor of the exponential argument
                      r(2) = argument exponent (pre-division)
      gudermannian:   r  = a scalar whose value is the numerator of
                           argument to gudermannian function:
                           GD(x) = atan(tanh(r/x))
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

`Logx`  - Logarithm base, a positive scalar    (default: natural)

`Lock`  - By default, FuzzEn2D only permits matrices with a maximum           size of 128 x 128 to prevent memory errors when storing data on RAM.            e.g. For Mat = [200 x 200], m = 3, and tau = 1, FuzzEn2D            creates a vector of 753049836 elements. To enable matrices           greater than [128 x 128] elements, set `Lock` to false.           (default: true)

```
      ` WARNING: unlocking the permitted matrix size may cause
      your Julia IDE to crash.`
```

# See also `SampEn2D`, `FuzzEn`, `XFuzzEn`

# References:

```
[1] Luiz Fernando Segato Dos Santos, et al.,
    "Multidimensional and fuzzy sample entropy (SampEnMF) for
    quantifying H&E histological images of colorectal cancer."
    Computers in biology and medicine 
    103 (2018): 148-160.

[2] Mirvana Hilal and Anne Humeau-Heurtier,
    "Bidimensional fuzzy entropy: Principle analysis and biomedical
    applications."
    41st Annual International Conference of the IEEE (EMBC) Society
    2019.

[3] Hamed Azami, et al.
    "Fuzzy Entropy Metrics for the Analysis of Biomedical Signals: 
    Assessment and Comparison"
    IEEE Access
    7 (2019): 104833-104847
```
