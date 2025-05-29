```
  SyDy, Zt = SyDyEn(Sig)
```

Returns the symbolic dynamic entropy (`SyDy`) and the symbolic sequence   (`Zt`) of the data sequence (`Sig`) using the default parameters:    embedding dimension = 2, time delay = 1, symbols = 3, logarithm = natural,   symbolic partition type = maximum entropy partitioning (`MEP`),    normalisation = normalises w.r.t # possible vector permutations (c^m) 

```
  SyDy, Zt = SyDyEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, c::Int=3, Typex::String="MEP", Logx::Real=exp(1), Norm::Bool=true)
```

Returns the symbolic dynamic entropy (`SyDy`) and the symbolic sequence   (`Zt`) of the data sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer  

`tau`   - Time Delay, a positive integer  

`c`     - Number of symbols, an integer > 1  

`Typex` - Type of symbolic sequnce partitioning method, one of the following:  

```
        {"linear","uniform","MEP"(default),"kmeans"}
```

`Logx`  - Logarithm base, a positive scalar    

`Norm`  - Normalisation of SyDyEn value: 

```
        [false]  no normalisation 
        [true]   normalises w.r.t # possible vector permutations (c^m+1) - default
```

See the EntropyHub guide for more info on these parameters.

# See also `DispEn`, `PermEn`, `CondEn`, `SampEn`, `MSEn`

# References:

```
  [1] Yongbo Li, et al.,
      "A fault diagnosis scheme for planetary gearboxes using 
      modified multi-scale symbolic dynamic entropy and mRMR feature 
      selection." 
      Mechanical Systems and Signal Processing 
      91 (2017): 295-312. 

  [2] Jian Wang, et al.,
      "Fault feature extraction for multiple electrical faults of 
      aviation electro-mechanical actuator based on symbolic dynamics
      entropy." 
      IEEE International Conference on Signal Processing, 
      Communications and Computing (ICSPCC), 2015.

  [3] Venkatesh Rajagopalan and Asok Ray,
      "Symbolic time series analysis via wavelet-based partitioning."
      Signal processing 
      86.11 (2006): 3309-3320.
```
