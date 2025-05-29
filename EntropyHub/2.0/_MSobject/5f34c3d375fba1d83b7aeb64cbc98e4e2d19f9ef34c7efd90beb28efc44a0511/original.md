```
Mobj = MSobject()
```

Returns a multiscale entropy object (`Mobj`) based on that originally  proposed by Costa et. al. (2002) using the following default parameters: EnType = SampEn(), embedding dimension = 2, time delay = 1,  radius = 0.2*SD(`Sig`), logarithm = natural

```
Mobj = MSobject(EnType::Function)
```

Returns a multiscale entropy object by passing the entropy function (`EnType`) and the specifying default parameters for that entropy function. To see the default parameters for a particular entropy method,           type:  `? EntropyHub.EnType`  

(e.g.  `? EntropyHub.SampEn`)

```
Mobj = MSobject(EnType::Function; kwargs...)
```

Returns a multiscale entropy object using the specified entropy method (`EnType`) and the 'keyword' parameters for that particular method. To see the default parameters for a particular entropy method,           type:   ? EntropyHub.EnType   (e.g.  ? EntropyHub.SampEn)

EnType can be any of the following entropy functions:

# Base Entropies:

```
-----------------
`ApEn`      - Approximate Entropy  

`SampEn`    - Sample Entropy   

`FuzzEn`    - Fuzzy Entropy    

`K2En`      - Kolmogorov Entropy   

`PermEn`    - Permutation Entropy	 

`CondEn`    - Conditional Entropy	   

`DistEn`    - Distribution Entropy	    

`DispEn`    - Dispersion Entropy	    

`SpecEn`    - Spectral Entropy   

`SyDyEn`    - Symbolic Dynamic Entropy	  

`IncrEn`    - Increment Entropy	    

`CoSiEn`    - Cosine Similarity Entropy	

`PhasEn`    - Phase Entropy	    

`SlopEn`    - Slope Entropy       

`BubbEn`    - Bubble Entropy   

`GridEn`    - Gridded Distribution Entropy  

`EnofEn`    - Entropy of Entropy	

`AttnEn`    - Attention Entropy    

`DivEn`     - Diversity Entropy 

`RangEn`    - Range Entropy
```

# Cross Entropies:

```
------------------
`XApEn`     - Cross-Approximate Entropy    

`XSampEn`   - Cross-Sample Entropy  

`XFuzzEn`   - Cross-Fuzzy Entropy   

`XK2En`     - Cross-Kolmogorov Entropy  

`XPermEn`   - Cross-Permutation Entropy   

`XCondEn`   - Cross-Conditional Entropy    

`XDistEn`   - Cross-Distribution Entropy    

`XSpecEn`   - Cross-Spectral Entropy
```

# Multivariate Entropies:

```
------------------
`MvSampEn`   - Multivariate Sample Entropy  

`MvFuzzEn`   - Multivariate Fuzzy Entropy   

`MvPermEn`   - Multivariate Permutation Entropy   

`MvCoSiEn`   - Multivariate Cosine Similarity Entropy    

`MvDispEn`   - Multivariate Dispersion Entropy
```

# See also `MSEn`, `XMSEn`, `MvMSEn`, `rMSEn`, `cMSEn`, `hMSEn`, `rXMSEn`, `cXMSEn`, `hXMSEn`, `cMvMSEn`
