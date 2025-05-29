```
Esp2D,  = EspEn2D(Mat)
```

Returns the bidimensional Espinosa entropy estimate (`Esp2D`)  estimated for the data matrix (`Mat`) using the default parameters:  time delay = 1, tolerance threshold = 20, percentage similarity = 0.7 logarithm = natural, matrix template size = [floor(H/10) floor(W/10)],  (where H and W represent the height (rows) and width (columns) of  the data matrix `Mat`)  ** The minimum number of rows and columns of `Mat` must be > 10.

```
Esp2D = EspEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10),             
                                tau::Int=1, r::Real=20, ps::Float=.7, Logx::Real=exp(1), Lock::Bool=true)
```

Returns the bidimensional Espinosa entropy (`Esp2D`) estimates for the data matrix (`Mat`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Template submatrix dimensions, an integer scalar (i.e. the same            height and width) or a two-element vector of integers [height, width] with a minimum value > 1.           (default: [floor(H/10) floor(W/10)]) 

`tau`   - Time Delay, a positive integer       (default: 1) 

`r`     - Tolerance threshold, a positive scalar  (default: 20) 

`ps`    - Percentage similarity, a value in range [0 1],  (default: 0.7) 

`Logx`  - Logarithm base, a positive scalar    (default: natural)  

`Lock`  - By default, EspEn2D only permits matrices with a maximum           size of 128 x 128 to prevent memory errors when storing data           on RAM. e.g. For Mat = [200 x 200], m = 3, and tau = 1,            EspEn2D creates a vector of 753049836 elements.            To enable matrices greater than [128 x 128] elements,           set `Lock` to false.  (default: true)  

```
      `WARNING: unlocking the permitted matrix size may cause your Julia
      IDE to crash.`
```

# See also `SampEn2D`, `FuzzEn2D`, `DispEn2D`, `DistEn2D`, `PermEn2D`

# References:

```
[1] Ricardo Espinosa, et al.,
    "Two-dimensional EspEn: A New Approach to Analyze Image Texture 
    by Irregularity." 
    Entropy,
    23:1261 (2021)
```
