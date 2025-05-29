```
MSx, CI = rMSEn(Sig, Mobj)
```

Returns a vector of refined multiscale entropy values (`MSx`) and the complexity  index (`CI`) of the data sequence (`Sig`) using the parameters specified by the multiscale object (`Mobj`) and the following default parameters: Scales = 3, Butterworth LPF Order = 6, Butterworth LPF cutoff frequency at scale (T): Fc = 0.5/T.  If the entropy function specified by `Mobj` is SampEn or ApEn, rMSEn  updates the threshold radius of the data sequence (Xt) at each scale to 0.2std(Xt) if no `r` value is provided by Mobj, or r.std(Xt) if `r` is specified.

```
MSx, CI = rMSEn(Sig::AbstractArray{T,1} where T<:Real, Mobj::NamedTuple; Scales::Int=3, 
                    F_Order::Int=6, F_Num::Float64=0.5, RadNew::Int=0, Plotx::Bool=false)
```

Returns a vector of refined multiscale entropy values (`MSx`) and the complexity  index (`CI`) of the data sequence (`Sig`) using the parameters specified by the multiscale object (`Mobj`) and the following 'keyword' arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1 (default = 3) 

`F_Order`  - Butterworth low-pass filter order, a positive integer              (default: 6) 

`F_Num`    - Numerator of Butterworth low-pass filter cutoff frequency,              a scalar value in range [0 < `F_Num` < 1]. The cutoff frequency              at each scale (T) becomes: Fc = `F_Num/T.  (default: 0.5) 

`RadNew`   - Radius rescaling method, an integer in the range [1 4].              When the entropy specified by `Mobj` is `SampEn` or `ApEn`,               `RadNew` allows the radius threshold to be updated at each               time scale (Xt). If a radius value is specified by `Mobj` (`r`),              this becomes the rescaling coefficient, otherwise it is set              to 0.2 (default). The value of `RadNew` specifies one of the               following methods:

```
         [1]    Standard Deviation          - r*std(Xt)

         [2]    Variance                    - r*var(Xt) 

         [3]    Mean Absolute Deviation     - r*mean_ad(Xt) 

         [4]    Median Absolute Deviation   - r*med_ad(Xt)
```

`Plotx`    - When `Plotx` == true, returns a plot of the entropy value at each              time scale (i.e. the multiscale entropy curve)  [default: false] 

# See also `MSobject`, `MSEn`, `cMSEn`, `hMSEn`, `SampEn`, `ApEn`, `XMSEn`

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

[4] José Fernando Valencia, et al.,
    "Refined multiscale entropy: Application to 24-h holter 
    recordings of heart period variability in healthy and aortic 
    stenosis subjects." 
    IEEE Transactions on Biomedical Engineering 
    56.9 (2009): 2202-2213.

[5] Puneeta Marwaha and Ramesh Kumar Sunkaria,
    "Optimal selection of threshold value ‘r’for refined multiscale
    entropy." 
    Cardiovascular engineering and technology 
    6.4 (2015): 557-576.
```
