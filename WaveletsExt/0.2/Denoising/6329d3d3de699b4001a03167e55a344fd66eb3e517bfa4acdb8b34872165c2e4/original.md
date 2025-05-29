```
denoiseall(x, inputtype, wt[; L=maxtransformlevels(size(x,1)),
    tree=maketree(size(x,1), L, :dwt), dnt=VisuShrink(size(x,1)),
    estnoise=noisest, bestTH=nothing, smooth=:regular])
```

Denoise multiple signals of input type `inputtype`. 

# Arguments:

  * `x::AbstractArray{<:Number}`: input signals/coefficients.
  * `inputtype::Symbol`: input type of `x`. Current accepted types of inputs are

      * `:sig`: original signals; `x` should be a 2-D array with each column    representing a signal.
      * `:dwt`: `dwt`-transformed signal coefficients; `x` should be a 2-D array    with each column representing the coefficients of a signal.
      * `:wpt`: `wpt`-transformed signal coefficients; `x` should be a 2-D array    with each column representing the coefficients of a signal.
      * `:sdwt`: `sdwt`-transformed signal coefficients; `x` should be a 3-D array   with each 2-D slice representing the coefficients of a signal.
      * `:swpd`: `swpd`-transformed signal coefficients; `x` should be a 3-D array   with each 2-D slice representing the coefficients of a signal.
      * `:acdwt`: `acdwt`-transformed signal coefficients from   AutocorrelationShell.jl; `x` should be a 3-D array with each 2-D slice    representing the coefficients of a signal.
      * `:acwpd`: `acwpd`-transformed signal coefficients from   AutocorrelationShell.jl; `x` should be a 3-D array with each 2-D slice    representing the coefficients of a signal.
  * `wt::Union{DiscreteWavelet, Nothing}`: the discrete wavelet to be used for   decomposition (for input type `:sig`) and reconstruction. `nothing` can    be supplied if no reconstruction is necessary.
  * `L::Integer`: the number of decomposition levels. Necessary for input types   `:sig`, `:dwt`, and `:sdwt`. Default value is set to be    `maxtransformlevels(size(x,1))`.
  * `tree::BitVector`: the decomposition tree of the signals. Necessary for input   types `:wpt` and `:swpd`. Default value is set to be    `maketree(size(x,1), L, :dwt)`.
  * `dnt::DNFT`: denoise type. Default type is set to be `VisuShrink(size(x,1))`.
  * `estnoise::Union{Function, Vector{<:Number}}`: noise estimation. Input can be   provided as a function to estimate noise in signal, or a vector of estimated   noise. Default is set to be the `noisest` function.
  * `bestTH::Union{Function, Nothing}`: method to determine the best threshold    value for a group of signals. If `nothing` is given, then each signal will   be denoised by its respective best threshold value determined from the    parameters `dnt` and `estnoise`; otherwise some function can be passed   to determine the best threshold value from a vector of threshold values, eg:   `mean` and `median`. Default is set to be `nothing`.
  * `smooth::Symbol`: the smoothing method used. `:regular` smoothing thresholds   all given coefficients, whereas `:undersmooth` smoothing does not threshold   the lowest frequency subspace node of the wavelet transform. Default is set   to be `:regular`.

**See alse:** [`denoise`](@ref), [`noisest`](@ref), [`relerrorthreshold`](@ref)
