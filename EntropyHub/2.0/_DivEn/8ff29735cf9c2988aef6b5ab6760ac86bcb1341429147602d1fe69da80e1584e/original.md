```
Div, CDEn, Bm = DivEn(Sig)
```

Returns the diversity entropy (`Div`), the cumulative diversity entropy (`CDEn`), and the corresponding probabilities (`Bm`) estimated from the data sequence (`Sig`)  using the default parameters:   embedding dimension = 2, time delay = 1, #bins = 5,  logarithm = natural,

```
Div, CDEn, Bm = DivEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Int=5, Logx::Real=exp(1))
```

Returns the diversity entropy (`Div`) estimated from the data sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1   

`tau`   - Time Delay, a positive integer    

`r`     - Histogram bins #: either 

```
        * an integer [1 < `r`] representing the number of bins
        * a list/numpy array of 3 or more increasing values in range [-1 1] representing the bin edges including the rightmost edge.
```

`Logx`  - Logarithm base, a positive scalar  (Enter 0 for natural logarithm)

# See also  `CoSiEn`, `PhasEn`, `SlopEn`, `GridEn`, `MSEn`

# References:

```
[1] X. Wang, S. Si and Y. Li, 
    "Multiscale Diversity Entropy: A Novel Dynamical Measure for Fault 
    Diagnosis of Rotating Machinery," 
    IEEE Transactions on Industrial Informatics,
    vol. 17, no. 8, pp. 5419-5429, Aug. 2021
    
[2] Y. Wang, M. Liu, Y. Guo, F. Shu, C. Chen and W. Chen, 
    "Cumulative Diversity Pattern Entropy (CDEn): A High-Performance, 
    Almost-Parameter-Free Complexity Estimator for Nonstationary Time Series,"
    IEEE Transactions on Industrial Informatics
    vol. 19, no. 9, pp. 9642-9653, Sept. 2023
```
