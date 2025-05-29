```
  MSx, CI = rXMSEn(Sig1, Sig2, Mobj)
```

Returns a vector of refined multiscale cross-entropy values (`MSx`) and   the complexity index (`CI`) between the data sequences contained in `Sig1` and `Sig2`   using the parameters specified by the multiscale object (`Mobj`) and the   following default parameters:   Scales = 3, Butterworth LPF Order = 6,   Butterworth LPF cutoff frequency at scale (T): Fc = 0.5/T.    If the entropy function specified by `Mobj` is `XSampEn` or `XApEn`,    `rMSEn` updates the threshold radius of the data sequences (Xt) at each scale   to 0.2*SDpooled(Xa, Xb) when no `r` value is provided by `Mobj`, or    `r`*SDpooled(Xa, Xb) if `r` is specified.

```
  MSx, CI = rXMSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple;
                   Scales::Int=3, F_Order::Int=6, F_Num::Float64=0.5, RadNew::Int=0, Plotx::Bool=false)
```

Returns a vector of refined multiscale cross-entropy values (`MSx`) and    the complexity index (`CI`) between the data sequences contained in `Sig1` and `Sig2`   using the parameters specified by the multiscale object (`Mobj`) and the   following keyword arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1 (default: 3)  

`F_Order`  - Butterworth low-pass filter order, a positive integer (default: 6)  

`F_Num`    - Numerator of Butterworth low-pass filter cutoff frequency,                a scalar value in range [0 < `F_Num` < 1]. The cutoff frequency                at each scale (T) becomes: Fc = `F_Num`/T.  (default: 0.5) 

`RadNew`   - Radius rescaling method, an integer in the range [1 4].                When the entropy specified by `Mobj` is `XSampEn` or `XApEn`,                 `RadNew` allows the radius threshold to be updated at each                 time scale (Xt). If a radius value is specified by `Mobj` (`r`),                this becomes the rescaling coefficient, otherwise it is set                to 0.2 (default). The value of `RadNew` specifies one of the                 following methods: 

```
           [1]    Pooled Standard Deviation          - r*std(Xt) 

           [2]    Pooled Variance                    - r*var(Xt) 

           [3]    Total Mean Absolute Deviation      - r*mean_ad(Xt) 

           [4]    Total Median Absolute Deviation    - r*med_ad(Xt)
```

`Plotx`    - When `Plotx` == true, returns a plot of the entropy value at                 each time scale (i.e. the multiscale entropy curve)                [default = false] 

# See also `MSobject`, `XMSEn`, `cXMSEn`, `hXMSEn`, `XSampEn`, `XApEn`, `MSEn`

# References:

```
  [1] Matthew W. Flood (2021), 
      "EntropyHub - An open source toolkit for entropic time series analysis"
      PLoS ONE 16(11):e0295448, 
      DOI:  10.1371/journal.pone.0259448
      https://www.EntropyHub.xyz

  [2]   Rui Yan, Zhuo Yang, and Tao Zhang,
      "Multiscale cross entropy: a novel algorithm for analyzing two
      time series." 
      5th International Conference on Natural Computation. 
      Vol. 1, pp: 411-413 IEEE, 2009.

  [3] José Fernando Valencia, et al.,
      "Refined multiscale entropy: Application to 24-h holter 
      recordings of heart period variability in healthy and aortic 
      stenosis subjects." 
      IEEE Transactions on Biomedical Engineering 
      56.9 (2009): 2202-2213.

  [4] Puneeta Marwaha and Ramesh Kumar Sunkaria,
      "Optimal selection of threshold value ‘r’for refined multiscale
      entropy." 
      Cardiovascular engineering and technology 
      6.4 (2015): 557-576.

  [5] Yi Yin, Pengjian Shang, and Guochen Feng, 
      "Modified multiscale cross-sample entropy for complex time 
      series."
      Applied Mathematics and Computation 
      289 (2016): 98-110.

  [6] Antoine Jamin, et al,
      "A novel multiscale cross-entropy method applied to navigation 
      data acquired with a bike simulator." 
      41st annual international conference of the IEEE EMBC
      IEEE, 2019.

  [7] Antoine Jamin and Anne Humeau-Heurtier. 
      "(Multiscale) Cross-Entropy Methods: A Review." 
      Entropy 
      22.1 (2020): 45.
```
