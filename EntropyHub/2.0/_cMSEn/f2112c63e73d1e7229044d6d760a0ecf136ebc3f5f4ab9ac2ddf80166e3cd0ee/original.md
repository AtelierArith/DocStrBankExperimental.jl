```
MSx, CI = cMSEn(Sig, Mobj)
```

Returns a vector of composite multiscale entropy values (`MSx`) for the data  sequence (`Sig`) using the parameters specified by the multiscale object  (`Mobj`) using the composite multiscale entropy method over 3 temporal scales.

```
MSx, CI = cMSEn(Sig::AbstractArray{T,1} where T<:Real, Mobj::NamedTuple;  
                    Scales::Int=3, RadNew::Int=0, Refined::Bool=false, Plotx::Bool=false)
```

Returns a vector of composite multiscale entropy values (`MSx`) of the  data sequence (`Sig`) using the parameters specified by the multiscale  object (`Mobj`) and the following 'keyword' arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3) 

`RadNew`   - Radius rescaling method, an integer in the range [1 4].              When the entropy specified by `Mobj` is `SampEn` or `ApEn`,               RadNew allows the radius threshold to be updated at each               time scale (Xt). If a radius value is specified by `Mobj` (`r`),              this becomes the rescaling coefficient, otherwise it is set              to 0.2 (default). The value of RadNew specifies one of the               following methods:

```
         [1]    Standard Deviation          - r*std(Xt)

         [2]    Variance                    - r*var(Xt) 

         [3]    Mean Absolute Deviation     - r*mean_ad(Xt) 

         [4]    Median Absolute Deviation   - r*med_ad(Xt)
```

`Refined`  - Refined-composite MSEn method. When `Refined == true` and the               entropy function specified by Mobj is `SampEn` or `FuzzEn`, cMSEn returns               the refined-composite multiscale entropy (rcMSEn) [default: false]

`Plotx`    - When `Plotx` == true, returns a plot of the entropy value at each             time scale (i.e. the multiscale entropy curve) [default: false]

# See also `MSobject`, `rMSEn`, `MSEn`, `hMSEn`, `SampEn`, `ApEn`, `XMSEn`

# References:

```
[1] Madalena Costa, Ary Goldberger, and C-K. Peng,
    "Multiscale entropy analysis of complex physiologic time series."
    Physical review letters
    89.6 (2002): 068102.

[2] Vadim V. Nikulin, and Tom Brismar,
    "Comment on “Multiscale entropy analysis of complex physiologic
    time series”." 
    Physical review letters 
    92.8 (2004): 089803.

[3] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
    "Costa, Goldberger, and Peng reply." 
    Physical Review Letters
    92.8 (2004): 089804.

 [4] Shuen-De Wu, et al.,
    "Time series analysis using composite multiscale entropy." 
    Entropy 
    15.3 (2013): 1069-1084.

[5] Shuen-De Wu, et al.,
    "Analysis of complex time series using refined composite 
    multiscale entropy." 
    Physics Letters A 
    378.20 (2014): 1369-1374.

[6] Azami, Hamed, Alberto Fernández, and Javier Escudero.
    "Refined multiscale fuzzy entropy based on standard deviation
    for biomedical signal analysis." 
    Medical & biological engineering & computing 55 (2017): 2037-2052.
```
