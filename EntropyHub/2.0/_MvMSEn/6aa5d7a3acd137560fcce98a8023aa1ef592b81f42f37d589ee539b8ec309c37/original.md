```
MSx, CI = MvMSEn(Data, Mobj)
```

Returns a vector of multivariate multiscale entropy values (`MSx`) and the complexity   index (`CI`) of the data sequences in `Data` using the parameters specified   by the multiscale object (`Mobj`) over 3 temporal scales with coarse-  graining (default). 

!!! note
    By default, the `MvSampEn` and `MvFuzzEn` multivariate entropy algorithms estimate entropy values using the "full"  method by comparing delay vectors  across all possible `m+1` expansions of the embedding space as applied in [1]. These methods are not lower-bounded to 0, like most entropy algorithms, so `MvMSEn` may return negative entropy values if the base multivariate  entropy function is `MvSampEn` and `MvFuzzEn`, even for stochastic processes...


---

```
MSx, CI = MSEn(Data::AbstractArray{T,2} where T<:Real, Mobj::NamedTuple; Scales::Int=3, Methodx::String="coarse", Plotx::Bool=false)
```

Returns a vector of multivariate multiscale entropy values (`MSx`) and the complexity   index (`CI`) of the data sequences in `Data` using the parameters specified by  the multiscale object (`Mobj`) and the following keyword arguments:

# Arguments:

`Scales`   - Number of temporal scales, an integer > 1   (default: 3) 

`Method`   - Graining method, one of the following: 

```
          {`coarse`,`modified`,`generalized`} [default = `coarse`]  
          For further info on these graining procedures, see the EntropyHub guide.
```

`Plotx`    - When Plotx == true, returns a plot of the entropy value at each               time scale (i.e. the multiscale entropy curve) [default: false]

!!! tip
    For further info on these graining procedures see the EntropyHub guide.


# See also  `MSobject`, `cMvMSEn`, `MvFuzzEn`, `MvSampEn`, `MvPermEn`, `MvCoSiEn`,  `MvDispEn`

# References:

```
[1] Ahmed Mosabber Uddin, Danilo P. Mandic
     "Multivariate multiscale entropy analysis."
     IEEE signal processing letters 19.2 (2011): 91-94.

[2] Madalena Costa, Ary Goldberger, and C-K. Peng,
     "Multiscale entropy analysis of complex physiologic time series."
     Physical review letters
     89.6 (2002): 068102.

[3] Vadim V. Nikulin, and Tom Brismar,
     "Comment on “Multiscale entropy analysis of complex physiologic
     time series”." 
     Physical Review Letters 
     92.8 (2004): 089803.

[4] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
     "Costa, Goldberger, and Peng reply." 
     Physical Review Letters
     92.8 (2004): 089804.

[5] Madalena Costa, Ary L. Goldberger and C-K. Peng,
     "Multiscale entropy analysis of biological signals." 
     Physical review E 
     71.2 (2005): 021906.

[6] Ranjit A. Thuraisingham and Georg A. Gottwald,
     "On multiscale entropy analysis for physiological data."
     Physica A: Statistical Mechanics and its Applications
     366 (2006): 323-332.

[7] Ahmed Mosabber Uddin, Danilo P. Mandic
     "Multivariate multiscale entropy: A tool for complexity
     analysis of multichannel data."
     Physical Review E 84.6 (2011): 061918.
```
