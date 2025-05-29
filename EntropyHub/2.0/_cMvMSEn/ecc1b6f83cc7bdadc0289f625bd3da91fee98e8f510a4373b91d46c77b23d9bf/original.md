```
MSx, CI = cMvMSEn(Data, Mobj)
```

Returns a vector of composite multivariate multiscale entropy values (`MSx`) and the complexity   index (`CI`) of the data sequences in `Data` using the parameters specified   by the multiscale object (`Mobj`) over 3 temporal scales with coarse-graining (default). 

!!! note
    By default, the `MvSampEn` and `MvFuzzEn` multivariate entropy algorithms estimate entropy values using the "full"  method by comparing delay vectors  across all possible `m+1` expansions of the embedding space as applied in [1]. These methods are not lower-bounded to 0, like most entropy algorithms, so `MvMSEn` may return negative entropy values if the base multivariate  entropy function is `MvSampEn` and `MvFuzzEn`, even for stochastic processes...


---

```
MSx, CI = cMvMSEn(Data, Mobj, Refined = True)
```

Returns a vector of refined-composite multiscale entropy values (`MSx`) for the data   sequences in (`Data`) using the parameters specified by the multiscale object   (`Mobj`) using the refined-composite multivariate multiscale entropy method (rcMSE) over 3 temporal  scales. When `Refined == true`, the base entropy method must be `MvSampEn` or `MvFuzzEn`.  If the entropy method is `MvSampEn`, cMvMSEn employs the method described in [1].   If the entropy method is `MvFuzzEn`, cMvMSEn employs the method described in [5]. 

```
MSx, CI = cMVMSEn(Data::AbstractArray{T,2} where T<:Real, Mobj::NamedTuple; Scales::Int=3, Refined::Bool="false", Plotx::Bool=false)
```

Returns a vector of multivariate multiscale entropy values (`MSx`) and the complexity   index (`CI`) of the data sequences in `Data` using the parameters specified by  the multiscale object (`Mobj`) and the following keyword arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3) 

`Refined`  - Refined-composite MvMSEn method.  When `Refined == True` and the                entropy function specified by `Mobj` is `MvSampEn` or `MvFuzzEn`,                `cMvMSEn` returns the refined-composite multivariate multiscale entropy (rcMSEn) [default: False]

`Plotx`    - When Plotx == true, returns a plot of the entropy value at each               time scale (i.e. the multiscale entropy curve) [default: false]

# See also  `MvMSEn`, `MSobject`, `MvFuzzEn`, `MvSampEn`, `MvPermEn`, `MvCoSiEn`,  `MvDispEn`

# References:

```
[1] Shuen-De Wu, et al.,
    "Time series analysis using composite multiscale entropy."
    Entropy
    15.3 (2013): 1069-1084.

[2] Shuen-De Wu, et al.,
    "Analysis of complex time series using refined composite
    multiscale entropy."
    Physics Letters A
    378.20 (2014): 1369-1374.

[3] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[4] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy analysis."
    IEEE signal processing letters 19.2 (2011): 91-94.

[5] Azami, Alberto Fernández, Javier Escudero.
    "Refined multiscale fuzzy entropy based on standard deviation for
    biomedical signal analysis."
    Medical & biological engineering & computing 55 (2017): 2037-2052.
```
