```
MCoSi, Bm = MvCoSiEn(Data)
```

Returns the multivariate cosine similarity entropy estimate (`MCoSi`)  and the corresponding global probabilities (`Bm`) estimated for the   M multivariate sequences in `Data` using the default parameters:   embedding dimension = 2*ones(M), time delay = ones(M),   angular threshold = 0.1, logarithm = 2, data normalization = none, 

!!! note
    To maximize the number of points in the embedding process, this algorithm  uses N-max(m * tau) delay vectors and **not** N-max(m) * max(tau) as employed  in [1][2].


---

```
MCoSi, Bm = MvCoSiEn(Data::AbstractArray{T,2} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, r::Real=.1, Logx::Real=2, Norm::Int=0)
```

Returns the multivariate cosine similarity entropy estimates (`MSamp`)   estimated from the M multivariate data sequences in `Data` using the   specified keyword arguments:

# Arguments:

`Data`    - Multivariate dataset, NxM matrix of N (>10) observations (rows) and M (cols) univariate data sequences

`m`       - Embedding Dimension, a vector of M positive integers

`tau`     - Time Delay, a vector of M positive integers

`r`     - Angular threshold, a value in range [0 < r < 1]   

`Logx`    - Logarithm base, a positive scalar (enter 0 for natural log) 

`Norm`    - Normalisation of `Data`, one of the following integers:

```
        *  [0]  no normalisation - default
        *  [1]  remove median(`Data`) to get zero-median series
        *  [2]  remove mean(`Data`) to get zero-mean series
        *  [3]  normalises each sequence in `Data` to unit variance and zero mean
        *  [4]  normalises each sequence in `Data` values to range [-1 1]
```

# See also  `CoSiEn`, `MvDispEn`, `MvSampEn`, `MvFuzzEn`, `MvPermEn`, `MSEn`

# References:

```
[1] H. Xiao, T. Chanwimalueang and D. P. Mandic, 
    "Multivariate Multiscale Cosine Similarity Entropy" 
    IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP),
    pp. 5997-6001, doi: 10.1109/ICASSP43922.2022.9747282.

[2] Xiao, H.; Chanwimalueang, T.; Mandic, D.P., 
    "Multivariate Multiscale Cosine Similarity Entropy and Its 
    Application to Examine Circularity Properties in Division Algebras."
    Entropy 2022, 24, 1287. 

[3] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[4] Theerasak Chanwimalueang and Danilo Mandic,
    "Cosine similarity entropy: Self-correlation-based complexity
    analysis of dynamical systems."
    Entropy 
    19.12 (2017): 652.
```
