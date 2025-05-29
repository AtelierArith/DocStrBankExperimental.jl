```
MPerm, MPnorm = MvPermEn(Data)
```

Returns the multivariate permutation entropy estimate (`MPerm`) and  the normalized permutation entropy for the M multivariate sequences in  `Data` using the default parameters:  embedding dimension = 2*ones(M,1), time delay = ones(M,1),   logarithm = 2, normalisation = w.r.t #symbols (sum(`m-1`))

!!! note
    The multivariate permutation entropy algorithm implemented here uses multivariate embedding based on Takens' embedding theorem, and follows the methods for multivariate entropy estimation through shared spatial  reconstruction as originally presented by Ahmed & Mandic [1]. 

    This function does **NOT** use the multivariate permutation entropy  algorithm of Morabito et al. (Entropy, 2012) where the entropy values of  individual univariate sequences are averaged because such methods do not follow the definition of multivariate embedding and therefore do not consider cross-channel statistical complexity.

    To maximize the number of points in the embedding process, this algorithm uses N- max(tau * m) delay vectors and **not** N-max(m) * max(tau) as employed in [1].


---

```
MPerm, MPnorm = MvPermEn(Data::AbstractArray{T} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, Typex::String="none", tpx::Union{Int,Nothing}=nothing, Norm::Bool=false, Logx::Real=2)
```

Returns the multivariate permutation entropy estimate (`MPerm`) for  the M multivariate data sequences in `Data` using the specified keyword arguments:

# Arguments:

`Data`  - Multivariate dataset, NxM matrix of N (>10) observations (rows) and M (cols) univariate data sequences

`m`     - Embedding Dimension, a vector of M positive integers

`tau`   - Time Delay, a vector of M positive integers

`Typex` - Permutation entropy variation, can be one of the following strings:

```
        {`'modified'`, `'ampaware'`, `'weighted'`, `'edge'`, `'phase'`}
        See the `EntropyHub guide <https://github.com/MattWillFlood/EntropyHub/blob/main/EntropyHub%20Guide.pdf>`_ for more info on MvPermEn variants.
```

`tpx`   - Tuning parameter for associated permutation entropy variation. 

```
        *   [ampaware]  `tpx` is the A parameter, a value in range [0 1]; default = 0.5
        *   [edge]      `tpx` is the r sensitivity parameter, a scalar > 0; default = 1
        *   [phase]     `tpx` is the option to unwrap the phase angle of Hilbert-transformed signal, either [] or 1 (default = 0)
```

`Norm`  - Normalisation of MPnorm value, a boolean operator:

```
        *   false -  normalises w.r.t log(# of permutation symbols [sum(m)-1]) - default
        *   true  -  normalises w.r.t log(# of all possible permutations [sum(m)!])
```

`Logx`   - Logarithm base, a positive scalar 

# See also    `PermEn`, `PermEn2D`, `XPermEn`, `MSEn`, `MvFuzzEn`, `MvSampEn`

# References:

```
[1] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[2] Christoph Bandt and Bernd Pompe, 
    "Permutation entropy: A natural complexity measure for time series." 
    Physical Review Letters,
    88.17 (2002): 174102.

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

[7] Maik Riedl, Andreas Müller, and Niels Wessel,
    "Practical considerations of permutation entropy." 
    The European Physical Journal Special Topics 
    222.2 (2013): 249-262.

[8] Kang Huan, Xiaofeng Zhang, and Guangbin Zhang,
    "Phase permutation entropy: A complexity measure for nonlinear time
    series incorporating phase information."
    Physica A: Statistical Mechanics and its Applications
    568 (2021): 125686.
```
