```
MSx, CI = cXMSEn(Sig1, Sig2, Mobj)
```

Returns a vector of composite multiscale cross-entropy values (`MSx`)  between two univariate data sequences contained in `Sig1` and `Sig2` using the  parameters specified by the multiscale object (`Mobj`) using the composite  multiscale method (cMSE) over 3 temporal scales.

```
MSx, CI = cXMSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple; 
                      Scales::Int=3, RadNew::Int=0, Refined::Bool=false, Plotx::Bool=false)
```

Returns a vector of composite multiscale cross-entropy values (`MSx`)  between the data sequences contained in `Sig1` and `Sig2` using the parameters specified by the multiscale object (`Mobj`) and the following keyword arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3)

`RadNew`   - Radius rescaling method, an integer in the range [1 4].              When the entropy specified by Mobj is `XSampEn` or `XApEn`,               RadNew rescales the radius threshold of the sub-sequences              at each time scale (Ykj). If a radius value is specified by              `Mobj` (`r`), this becomes the rescaling coefficient, otherwise              it is set to 0.2 (default). The value of RadNew specifies              one of the following methods:

```
         [1]    Pooled Standard Deviation          - r*std(Ykj)

         [2]    Pooled Variance                    - r*var(Ykj)

         [3]    Total Mean Absolute Deviation      - r*mean_ad(Ykj)

         [4]    Total Median Absolute Deviation    - r*med_ad(Ykj,1)
```

`Refined`  - Refined-composite XMSEn method. When `Refined` == true and the               entropy function specified by `Mobj` is `XSampEn` or `XFuzzEn`, cXMSEn              returns the refined-composite multiscale entropy (rcXMSEn).              (default: false) `Plotx`    - When `Plotx` == true, returns a plot of the entropy value at each               time scale (i.e. the multiscale entropy curve) [default: false]

# See also `MSobject`, `XMSEn`, `rXMSEn`, `hXMSEn`, `XSampEn`, `XApEn`, `cMSEn`

# References:

```
[1] Rui Yan, Zhuo Yang, and Tao Zhang,
    "Multiscale cross entropy: a novel algorithm for analyzing two
    time series." 
    5th International Conference on Natural Computation. 
    Vol. 1, pp: 411-413 IEEE, 2009.

[2] Yi Yin, Pengjian Shang, and Guochen Feng, 
    "Modified multiscale cross-sample entropy for complex time 
    series."
    Applied Mathematics and Computation 
    289 (2016): 98-110.

[3] Madalena Costa, Ary Goldberger, and C-K. Peng,
    "Multiscale entropy analysis of complex physiologic time series."
    Physical review letters
    89.6 (2002): 068102.

[4] Antoine Jamin, et al,
    "A novel multiscale cross-entropy method applied to navigation 
    data acquired with a bike simulator." 
    41st annual international conference of the IEEE EMBC
    IEEE, 2019.

[5] Antoine Jamin and Anne Humeau-Heurtier. 
    "(Multiscale) Cross-Entropy Methods: A Review." 
    Entropy 
    22.1 (2020): 45.

[6] Shuen-De Wu, et al.,
    "Time series analysis using composite multiscale entropy." 
    Entropy 
    15.3 (2013): 1069-1084.
```
