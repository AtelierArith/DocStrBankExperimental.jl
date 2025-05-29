```
Perm, Pnorm, cPE = PermEn(Sig)
```

Returns the permuation entropy estimates `Perm`, the normalised permutation entropy `Pnorm` and the conditional permutation entropy `cPE` for `m` = [1,2] estimated from the data sequence `Sig`  using the default  parameters: embedding dimension = 2, time delay = 1, logarithm = base 2,  normalisation = w.r.t #symbols (`m`-1) Note: using the standard PermEn estimation, `Perm` = 0 when `m` = 1. Note: It is recommeneded that signal length > 5m! (see [8] and Amigo et al., Europhys. Lett. 83:60005, 2008)

```
Perm, Pnorm, cPE = PermEn(Sig, m)
```

Returns the permutation entropy estimates `Perm` estimated from the data sequence `Sig` using the specified embedding dimensions = [1,...,`m`]  with other default parameters as listed above.

```
Perm, Pnorm, cPE = PermEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Typex::String="none", tpx::Union{Real,Nothing}=nothing, Logx::Real=2, Norm::Bool=false)
```

Returns the permutation entropy estimates `Perm` for dimensions = [1,...,`m`] estimated from the data sequence `Sig` using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1 

`tau`   - Time Delay, a positive integer

`Logx`  - Logarithm base, a positive scalar (enter 0 for natural log) 

`Norm`  - Normalisation of PermEn value:

```
      false -  normalises w.r.t log(# of permutation symbols [m-1]) - default
      true  -  normalises w.r.t log(# of all possible permutations [m!])
      * Note: Normalised permutation entropy is undefined for m = 1.
      ** Note: When Typex = 'uniquant' and Norm = true, normalisation
      is calculated w.r.t. log(tpx^m)
```

`Typex`  - Permutation entropy variation, one of the following:           {`"none", "uniquant", "finegrain", "modified", "ampaware",           "weighted", "edge", "phase"}           See the EntropyHub guide for more info on PermEn variations.    

`tpx`   - Tuning parameter for associated permutation entropy variation.

```
      [uniquant]  'tpx' is the L parameter, an integer > 1 (default = 4).           
      [finegrain] 'tpx' is the alpha parameter, a positive scalar (default = 1)
      [ampaware]  'tpx' is the A parameter, a value in range [0 1] (default = 0.5)
      [edge]      'tpx' is the r sensitivity parameter, a scalar > 0 (default = 1)
      [phase]     'tpx' unwraps the instantaneous phase (angle of analytic signal) when tpx==1 (default = 0)
      See the EntropyHub guide for more info on PermEn variations.
```

# See also `XPermEn`, `MSEn`, `XMSEn`, `SampEn`, `ApEn`, `CondEn`

# References:

```
[1] Christoph Bandt and Bernd Pompe, 
        "Permutation entropy: A natural complexity measure for time series." 
        Physical Review Letters,
        88.17 (2002): 174102.

[2] Xiao-Feng Liu, and Wang Yue,
        "Fine-grained permutation entropy as a measure of natural 
        complexity for time series." 
        Chinese Physics B 
        18.7 (2009): 2690.

[3] Chunhua Bian, et al.,
        "Modified permutation-entropy analysis of heartbeat dynamics."
        Physical Review E
        85.2 (2012) : 021906

[4] Bilal Fadlallah, et al.,
        "Weighted-permutation entropy: A complexity measure for time 
        series incorporating amplitude information." 
        Physical Review E 
        87.2 (2013): 022911.

[5] Hamed Azami and Javier Escudero,
        "Amplitude-aware permutation entropy: Illustration in spike 
        detection and signal segmentation." 
        Computer methods and programs in biomedicine,
        128 (2016): 40-51.

[6] Zhiqiang Huo, et al.,
        "Edge Permutation Entropy: An Improved Entropy Measure for 
        Time-Series Analysis," 
        45th Annual Conference of the IEEE Industrial Electronics Soc,
        (2019), 5998-6003

[7] Zhe Chen, et al. 
        "Improved permutation entropy for measuring complexity of time
        series under noisy condition." 
        Complexity 
        1403829 (2019).

[8] Maik Riedl, Andreas Müller, and Niels Wessel,
        "Practical considerations of permutation entropy." 
        The European Physical Journal Special Topics 
        222.2 (2013): 249-262.

[9] Kang Huan, Xiaofeng Zhang, and Guangbin Zhang,
        "Phase permutation entropy: A complexity measure for nonlinear time 
        series incorporating phase information." 
        Physica A: Statistical Mechanics and its Applications 
        568 (2021): 125686.
```
