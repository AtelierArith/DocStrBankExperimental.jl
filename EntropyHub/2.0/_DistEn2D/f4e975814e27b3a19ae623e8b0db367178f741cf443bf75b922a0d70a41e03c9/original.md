```
Dist2D = DistEn2D(Mat)
```

Returns the bidimensional distribution entropy estimate (`Dist2D`) estimated for the data matrix (`Mat`) using the default parameters: time delay = 1, histogram binning method = "sturges", logarithm = natural,  template matrix size = [floor(H/10) floor(W/10)], (where H and W represent the height (rows) and width (columns) of the data matrix `Mat`) 

** The minimum number of rows and columns of Mat must be > 10.**

```
Dist2D = DistEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10), tau::Int=1,
                    Bins::Union{Int,String}="Sturges", Logx::Real=2, Norm::Int=2, Lock::Bool=true)
```

Returns the bidimensional distribution entropy (`Dist2D`) estimate for  the data matrix (`Mat`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Template submatrix dimensions, an integer scalar (i.e. the same           height and width) or a two-element tuple of integers            [height, width] with a minimum value > 1.           [default: [floor(H/10) floor(W/10)]] 

`tau`   - Time Delay, a positive integer       [default: 1]  

`Bins`  - Histogram bin selection method for distance distribution,           an integer > 1 indicating the number of bins, or one of the            following strings {`"sturges", "sqrt", "rice", "doanes"``}           [default: 'sturges']  

`Logx`  - Logarithm base, a positive scalar        [default: natural]

```
      ** enter 0 for natural logarithm.**
```

`Norm`  - Normalisation of `Dist2D` value, one of the following integers:           [0]  no normalisation.           [1]  normalises values of data matrix (`Mat`) to range [0 1].           [2]  normalises values of data matrix (`Mat`) to range [0 1],                and normalises the distribution entropy value (`Dist2D`)                w.r.t the number of histogram bins.  [default]           [3]  normalises the distribution entropy value                w.r.t the number of histogram bins, without normalising                data matrix values. 

`Lock`  - By default, DistEn2D only permits matrices with a maximum           size of 128 x 128 to prevent memory errors when storing data on RAM.            e.g. For Mat = [200 x 200], m = 3, and tau = 1, DistEn2D            creates a vector of 753049836 elements. To enable matrices           greater than [128 x 128] elements, set `Lock` to false.           [default: 'true']           `WARNING: unlocking the permitted matrix size may cause your Julia            IDE to crash.`

# See also `DistEn`, `XDistEn`, `SampEn2D`, `FuzzEn2D`, `MSEn`

# References:

```
[1] Hamed Azami, Javier Escudero and Anne Humeau-Heurtier,
    "Bidimensional distribution entropy to analyze the irregularity
    of small-sized textures."
    IEEE Signal Processing Letters 
    24.9 (2017): 1338-1342.
```
