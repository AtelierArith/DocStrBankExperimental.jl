```
SE2D, Phi1, Phi2 = SampEn2D(Mat)
```

Returns the bidimensional sample entropy estimate (`SE2D`) and the number of matched sub-matricess (m:Phi1, m+1:Phi2) estimated for the data  matrix (`Mat`) using the default parameters: time delay = 1, radius distance threshold = 0.2*SD(`Mat`), logarithm = natural matrix template size = [floor(H/10) floor(W/10)], (where H and W represent the height (rows) and width (columns) of the data matrix `Mat`) 

** The minimum dimension size of Mat must be > 10.**

```
SE2D, Phi1, Phi2 = SampEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10),             
                                tau::Int=1, r::Real=0.2*std(Mat,corrected=false), Logx::Real=exp(1), Lock::Bool=true)
```

Returns the bidimensional sample entropy (`SE2D`) estimates for the data matrix (`Mat`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Template submatrix dimensions, an integer scalar (i.e. the same            height and width) or a two-element vector of integers            [height, width] with a minimum value > 1.           (default: [floor(H/10) floor(W/10)]) 

`tau`   - Time Delay, a positive integer       (default: 1) 

`r`     - Distance Threshold, a positive scalar  (default: 0.2*SD(Mat)) 

`Logx`  - Logarithm base, a positive scalar    (default: natural)  

`Lock`  - By default, SampEn2D only permits matrices with a maximum           size of 128 x 128 to prevent memory errors when storing data           on RAM. e.g. For Mat = [200 x 200], m = 3, and tau = 1,            SampEn2D creates a vector of 753049836 elements.            To enable matrices greater than [128 x 128] elements,           set `Lock` to false.  (default: true)  

```
      `WARNING: unlocking the permitted matrix size may cause your Julia
      IDE to crash.`
```

# See also `SampEn`, `FuzzEn2D`, `XSampEn`, `MSEn`

# References:

```
[1] Luiz Eduardo Virgili Silva, et al.,
     "Two-dimensional sample entropy: Assessing image texture 
     through irregularity." 
     Biomedical Physics & Engineering Express
     2.4 (2016): 045002.
```
