```
  MSx, Sn, CI = hXMSEn(Sig1, Sig2, Mobj)
```

Returns a vector of cross-entropy values (`MSx`) calculated at each node    in the hierarchical tree, the average cross-entropy value across all    nodes at each scale (`Sn`), and the complexity index (`CI`) of the hierarchical    tree (i.e. sum(`Sn`)) between the data sequences contained in `Sig1` and `Sig2` using   the parameters specified by the multiscale object (`Mobj`) over 3 temporal   scales (default).   The entropy values in `MSx` are ordered from the root node (S.00) to the   Nth subnode at scale T (S.TN): i.e. S.00, S.10, S.11, S.20, S.21, S.22,   S.23, S.30, S.31, S.32, S.33, S.34, S.35, S.36, S.37, S.40, ... , S.TN.   The average cross-entropy values in Sn are ordered in the same way, with the   value of the root node given first: i.e. S0, S1, S2, ..., ST

```
  MSx, Sn, CI = hXMSEn(Sig1::AbstractVector{T} where T<:Real, Sig2::AbstractVector{T} where T<:Real, Mobj::NamedTuple; 
                           Scales::Int=3, RadNew::Int=0, Plotx::Bool=false)
```

Returns a vector of cross-entropy values (`MSx`) calculated at each node    in the hierarchical tree, the average cross-entropy value across all   nodes at each scale (`Sn`), and the complexity index (`CI`) of the entire   hierarchical tree between the data sequences contained in `Sig1` and `Sig2` using    the following name/value pair arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3)                At each scale (T), entropy is estimated for 2^(T-1) nodes. 

`RadNew`   - Radius rescaling method, an integer in the range [1 4].                When the entropy specified by `Mobj` is `XSampEn` or `XApEn`,                 `RadNew` allows the radius threshold to be updated at each                 node in the tree. If a radius value is specified by `Mobj` (`r`),                this becomes the rescaling coefficient, otherwise it is set                to 0.2 (default). The value of `RadNew` specifies one of the                 following methods: 

```
           [1]    Pooled Standard Deviation          - r*std(Xt) 

           [2]    Pooled Variance                    - r*var(Xt) 

           [3]    Total Mean Absolute Deviation      - r*mean_ad(Xt) 

           [4]    Total Median Absolute Deviation    - r*med_ad(Xt)
```

`Plotx`    - When `Plotx` == true, returns a plot of the average cross-entropy                 value at each time scale (i.e. the multiscale entropy curve)                and a hierarchical graph showing the entropy value of each node                in the hierarchical tree decomposition.  (default: false) 

# See also `MSobject`, `XMSEn`, `rXMSEn`, `cXMSEn`, `XSampEn`, `XApEn`, `hMSEn`

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

  [3] Ying Jiang, C-K. Peng and Yuesheng Xu,
      "Hierarchical entropy analysis for biological signals."
      Journal of Computational and Applied Mathematics
      236.5 (2011): 728-742.
```
