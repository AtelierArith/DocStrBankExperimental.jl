```
 MSx, CI = MSEn(Sig, Mobj)
```

Returns a vector of multiscale entropy values `MSx` and the complexity   index `CI` of the data sequence `Sig` using the parameters specified   by the multiscale object `Mobj` over 3 temporal scales with coarse-  graining (default). 

```
 MSx, CI = MSEn(Sig::AbstractArray{T,1} where T<:Real, Mobj::NamedTuple; Scales::Int=3, 
                      Methodx::String="coarse", RadNew::Int=0, Plotx::Bool=false)
```

Returns a vector of multiscale entropy values `MSx` and the complexity   index `CI` of the data sequence `Sig` using the parameters specified by  the multiscale object `Mobj` and the following 'keyword' arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3) 

`Method`   - Graining method, one of the following:                {`coarse`,`modified`,`imf`,`timeshift`,`generalized`} [default = `coarse`]                 For further info on these graining procedures, see the EntropyHub guide.  

`RadNew`   - Radius rescaling method, an integer in the range [1 4].               When the entropy specified by `Mobj` is `SampEn` or `ApEn`,                RadNew allows the radius threshold to be updated at each                time scale (Xt). If a radius value is specified by `Mobj` (`r`),               this becomes the rescaling coefficient, otherwise it is set               to 0.2 (default). The value of RadNew specifies one of the                following methods:

```
          [1]    Standard Deviation          - r*std(Xt)

          [2]    Variance                    - r*var(Xt) 

          [3]    Mean Absolute Deviation     - r*mean_ad(Xt) 

          [4]    Median Absolute Deviation   - r*med_ad(Xt)
```

`Plotx`    - When Plotx == true, returns a plot of the entropy value at each               time scale (i.e. the multiscale entropy curve) [default: false]

`For further info on these graining procedures see the EntropyHub guide.`

# See also `MSobject`, `rMSEn`, `cMSEn`, `hMSEn`, `SampEn`, `ApEn`, `XMSEn`

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

 [4] Madalena Costa, Ary L. Goldberger and C-K. Peng,
         "Multiscale entropy analysis of biological signals." 
         Physical review E 
         71.2 (2005): 021906.

 [5] Ranjit A. Thuraisingham and Georg A. Gottwald,
         "On multiscale entropy analysis for physiological data."
         Physica A: Statistical Mechanics and its Applications
         366 (2006): 323-332.

 [6] Meng Hu and Hualou Liang,
         "Intrinsic mode entropy based on multivariate empirical mode
         decomposition and its application to neural data analysis." 
         Cognitive neurodynamics
         5.3 (2011): 277-284.

 [7] Anne Humeau-Heurtier 
         "The multiscale entropy algorithm and its variants: A review." 
         Entropy 
         17.5 (2015): 3110-3123.

 [8] Jianbo Gao, et al.,
         "Multiscale entropy analysis of biological signals: a 
         fundamental bi-scaling law." 
         Frontiers in computational neuroscience 
         9 (2015): 64.

 [9]  Paolo Castiglioni, et al.,
         "Multiscale Sample Entropy of cardiovascular signals: Does the
         choice between fixed-or varying-tolerance among scales 
         influence its evaluation and interpretation?." 
         Entropy
         19.11 (2017): 590.

 [10] Tuan D Pham,
         "Time-shift multiscale entropy analysis of physiological signals." 
         Entropy 
         19.6 (2017): 257.

 [11] Hamed Azami and Javier Escudero,
         "Coarse-graining approaches in univariate multiscale sample 
         and dispersion entropy." 
         Entropy 20.2 (2018): 138.

 [12] Madalena Costa and Ary L. Goldberger,
         "Generalized multiscale entropy analysis: Application to quantifying 
         the complex volatility of human heartbeat time series." 
         Entropy 17.3 (2015): 1197-1203.
```
