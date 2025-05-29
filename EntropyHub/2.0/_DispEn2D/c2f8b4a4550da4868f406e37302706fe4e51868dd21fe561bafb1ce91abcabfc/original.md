```
Disp2D, RDE = DispEn2D(Mat)
```

Returns the bidimensional dispersion entropy estimate (`Disp2D`) and reverse bidimensional dispersion entropy (`RDE`) estimated for the data matrix (`Mat`)  using the default parameters:  time delay = 1, symbols = 3, logarithm = natural,  data transform = normalised cumulative density function (`'ncdf'`), logarithm = natural,  template matrix size = [floor(H/10) floor(W/10)], (where H and W represent the height (rows) and width (columns) of the data matrix `Mat`) 

** The minimum number of rows and columns of Mat must be > 10.**

```
Disp2D, RDE = DispEn2D(Mat::AbstractArray{T,2} where T<:Real; 
                    m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10), tau::Int=1,
                        c::Int=3, Typex::String="ncdf", Logx::Real=exp(1), Norm::Bool=false, Lock::Bool=true)
```

Returns the bidimensional dispersion entropy (`Disp2D`) and reverse  bidimensional distribution entropy (`RDE`) estimate for the data matrix (`Mat`)  using the specified 'keyword' arguments:

# Arguments:

`m`     - Template submatrix dimensions, an integer scalar (i.e. the same           height and width) or a two-element tuple of integers            [height, width] with a minimum value > 1.           [default: [floor(H/10) floor(W/10)]] 

`tau`   - Time Delay, a positive integer       [default: 1]  

`c`     - Number of symbols, an integer > 1 `Typex` - Type of symbolic mapping transform, one of the following:           {`linear`, `kmeans`, `ncdf`, `equal`}           See the `EntropyHub Guide` for more info on these transforms.     `Logx`  - Logarithm base, a positive scalar        [default: natural]

```
      ** enter 0 for natural logarithm.**
```

`Norm`  - Normalisation of `Disp2D` value, a boolean:             - [false]   no normalisation - default             - [true]    normalises w.r.t number of possible dispersion patterns.     `Lock`  - By default, DispEn2D only permits matrices with a maximum           size of 128 x 128 to prevent memory errors when storing data on RAM.            e.g. For Mat = [200 x 200], m = 3, and tau = 1, DispEn2D            creates a vector of 753049836 elements. To enable matrices           greater than [128 x 128] elements, set `Lock` to false.           [default: 'true']           `WARNING: unlocking the permitted matrix size may cause your Julia            IDE to crash.`

# See also `DispEn`, `DistEn2D`, `SampEn2D`, `FuzzEn2D`, `MSEn`

# References:

```
[1] Hamed Azami, et al.,
    "Two-dimensional dispersion entropy: An information-theoretic 
    method for irregularity analysis of images."
    Signal Processing: Image Communication, 
    75 (2019): 178-187.
```
