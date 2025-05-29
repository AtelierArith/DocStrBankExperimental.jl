```
MSamp, B0, Bt, B1 = MvSampEn(Data)
```

Returns the multivariate sample entropy estimate (`MSamp`) and the  average number of matched delay vectors (`m`: `B0`; joint total   `m+1` subspace: `Bt`; all possible `m+1` subspaces: `B1`),  from the M multivariate sequences in `Data` using the default parameters:   embedding dimension = 2*ones(M), time delay = ones(M), radius threshold = 0.2,  logarithm = natural, data normalization = false

!!! note
    The entropy value returned as `MSamp` is estimated using the "full"  method [i.e.  -log(Bt/B0)] which compares delay vectors across all possible `m+1`  expansions of the embedding space as applied in [1][2]. Contrary to conventional definitions of sample entropy, this method does not provide a lower bound of 0!! Thus, it is possible to obtain negative entropy values for multivariate  sample entropy, even for stochastic processes...

    Alternatively, one can calculate `MSamp` via the "naive" method,  which ensures a lower bound of 0, by using the average number of matched vectors for an individual `m+1` subspace (B1) [e.g. -log(B1(1)/B0)], or the average for all `m+1` subspaces [i.e. -log(mean(B1)/B0)].

    To maximize the number of points in the embedding process, this algorithm  uses N - max(m * tau) delay vectors and ***not*** N-max(m) * max(tau) as employed  in [1][2].


---

```
MSamp, B0, Bt, B1 = MvSampEn(Data::AbstractArray{T} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, r::Real=0.2, Logx::Real=exp(1), Norm::Bool=false)
```

Returns the multivariate sample entropy estimates (`MSamp`) estimated  from the M multivariate data sequences in `Data` using the specified   keyword arguments:

# Arguments:

`Data`  - Multivariate dataset, NxM matrix of N (>10) observations (rows) and M (cols) univariate data sequences

`m`     - Embedding Dimension, a vector of M positive integers

`tau`   - Time Delay, a vector of M positive integers

`r`     - Radius Distance Threshold, a positive scalar  

`Logx`  - Logarithm base, a positive scalar 

`Norm`  - Normalisation of all M sequences to unit variance, a boolean

# See also `SampEn`, `XSampEn`, `SampEn2D`, `MSEn`, `MvFuzzEn`, `MvPermEn`

# References:

```
[1] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[2] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy analysis."
    IEEE signal processing letters 19.2 (2011): 91-94.
```
