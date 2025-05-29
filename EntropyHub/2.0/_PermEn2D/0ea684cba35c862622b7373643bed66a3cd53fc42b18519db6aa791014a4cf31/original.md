```
   Perm2D = PermEn2D(Mat)
```

Returns the bidimensional permutation entropy estimate (`Perm2D`) estimated for     the data matrix (`Mat`) using the default parameters: time delay = 1,    logarithm = natural, template matrix size = [floor(H/10) floor(W/10)],      (where H and W represent the height (rows) and width (columns) of the data matrix `Mat`) 

** The minimum dimension size of Mat must be > 10.**

```
   Perm2D = PermEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10),             
                                   tau::Int=1, Norm::Bool=true, Logx::Real=exp(1), Lock::Bool=true)
```

Returns the bidimensional permutation entropy (`Perm2D`) estimates for the data    matrix (`Mat`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Template submatrix dimensions, an integer scalar (i.e. the same               height and width) or a two-element vector of integers               [height, width] with a minimum value > 1.              (default: [floor(H/10) floor(W/10)]) 

`tau`   - Time Delay, a positive integer       (default: 1) 

`Norm`  - Normalization of permutation entropy estimate, a boolean  (default: true) 

`Logx`  - Logarithm base, a positive scalar    (default: natural)  

`Lock`  - By default, PermEn2D only permits matrices with a maximum              size of 128 x 128 to prevent memory errors when storing data              on RAM. e.g. For Mat = [200 x 200], m = 3, and tau = 1,               SampEn2D creates a vector of 753049836 elements.               To enable matrices greater than [128 x 128] elements,              set `Lock` to false.  (default: true)  

```
         `WARNING: unlocking the permitted matrix size may cause your Julia
         IDE to crash.`
```

**NOTE** - The original bidimensional permutation entropy algorithms               [1][2] do not account for equal-valued elements of the embedding              matrices.               To overcome this, `PermEn2D` uses the lowest common rank for              such instances. For example, given an embedding matrix A where,              A = [3.4  5.5  7.3]                  |2.1  6    9.9|                  [7.3  1.1  2.1]              would normally be mapped to an ordinal pattern like so,              [3.4  5.5  7.3  2.1  6  9.9  7.3  1.1  2.1] =>              [ 8    4    9    1   2   5    3    7    6 ]              However, indices 4 & 9, and 3 & 7 have the same values, 2.1              and 7.3 respectively. Instead, PermEn2D uses the ordinal pattern              [ 8    4    4    1   2   5    3    3    6 ]              where the lowest rank (4 & 3) are used instead (of 9 & 7).               Therefore, the number of possible permutations is no longer               (mx*my)!, but (mx*my)^(mx*my). Here, the PermEn2D value is               normalized by the maximum Shannon entropy (Smax = log((mx*my)!)               $assuming that no equal values are found in the permutation              motif matrices$, as presented in [1].

# See also `SampEn2D`, `FuzzEn2D`, `DispEn2D`, `DistEn2D`

# References:

```
   [1] Haroldo Ribeiro et al.,
           "Complexity-Entropy Causality Plane as a Complexity Measure 
           for Two-Dimensional Patterns"
           PLoS ONE (2012), 7(8):e40689, 

   [2] Luciano Zunino and Haroldo Ribeiro,
           "Discriminating image textures with the multiscale
           two-dimensional complexity-entropy causality plane"
           Chaos, Solitons and Fractals,  91:679-688 (2016)

   [3] Matthew Flood and Bernd Grimm,
           "EntropyHub: An Open-source Toolkit for Entropic Time Series Analysis"
           PLoS ONE (2021) 16(11): e0259448.
```
