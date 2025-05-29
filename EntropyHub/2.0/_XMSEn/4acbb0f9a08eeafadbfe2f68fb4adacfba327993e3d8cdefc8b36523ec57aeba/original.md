```
MSx, CI = XMSEn(Sig1, Sig2, Mobj)
```

Returns a vector of multiscale cross-entropy values `MSx` and the complexity  index `CI` between the data sequences contained in `Sig1` and `Sig2` using the parameters  specified by the multiscale object `Mobj` over 3 temporal scales with coarse- graining `default`. 

```
MSx,CI = MSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple; 
                 Scales::Int=3, Methodx::String="coarse", RadNew::Int=0, Plotx::Bool=false)
```

Returns a vector of multiscale cross-entropy values `MSx` and the complexity  index `CI` of the data sequences contained in `Sig1` and `Sig2` using the parameters  specified by the multiscale object `Mobj` and the following 'keyword' arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3) 

`Method`   - Graining method, one of the following:

```
         {`"coarse", "modified", "imf", "timeshift","generalized"`}  [default: 'coarse'] 
         For further info on graining procedures, see the Entropyhub guide.
```

`RadNew`   - Radius rescaling method, an integer in the range [1 4].              When the entropy specified by `Mobj` is `XSampEn` or `XApEn`,               `RadNew` allows the radius threshold to be updated at each               time scale (Xt). If a radius value is specified by `Mobj` (`r`),              this becomes the rescaling coefficient, otherwise it is set              to 0.2 (default). The value of `RadNew` specifies one of the               following methods: 

```
         [1]    Pooled Standard Deviation          - r*std(Xt) 

         [2]    Pooled Variance                    - r*var(Xt) 

         [3]    Total Mean Absolute Deviation      - r*mean_ad(Xt) 

         [4]    Total Median Absolute Deviation    - r*med_ad(Xt)
```

`Plotx`    - When `Plotx` == true, returns a plot of the entropy value at each              time scale (i.e. the multiscale entropy curve)  [default: false]

`For further info on these graining procedures see the EntropyHub guide.`

# See also `MSobject`, `MSEn`, `cXMSEn`, `rXMSEn`, `hXMSEn`, `XSampEn`, `XApEn`, `XFuzzEn`

# References:

```
[1] Rui Yan, Zhuo Yang, and Tao Zhang,
    "Multiscale cross entropy: a novel algorithm for analyzing two
    time series." 
    5th International Conference on Natural Computation. 
    Vol. 1, pp: 411-413 IEEE, 2009.

[2] Madalena Costa, Ary Goldberger, and C-K. Peng,
    "Multiscale entropy analysis of complex physiologic time series."
    Physical review letters
    89.6 (2002): 068102.

[3] Vadim V. Nikulin, and Tom Brismar,
    "Comment on “Multiscale entropy analysis of complex physiologic
    time series”." 
    Physical review letters 
    92.8 (2004): 089803.

[4] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
    "Costa, Goldberger, and Peng reply." 
    Physical Review Letters
    92.8 (2004): 089804.

[5] Antoine Jamin, et al,
    "A novel multiscale cross-entropy method applied to navigation 
    data acquired with a bike simulator." 
    41st annual international conference of the IEEE EMBC
    IEEE, 2019.

[6] Antoine Jamin and Anne Humeau-Heurtier. 
    "(Multiscale) Cross-Entropy Methods: A Review." 
    Entropy 
    22.1 (2020): 45.
```
