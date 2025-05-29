```
MDisp, RDE = MvDispEn(Data)
```

Returns the multivariate dispersion entropy estimate (`MDisp`) and  the reverse dispersion entropy (`RDE`) for the M multivariate sequences   in `Data` using the default parameters:  embedding dimension = 2*ones(M,1), time delay = ones(M,1), # symbols = 3,   algorithm method = "v1" (see below), data transform = normalised cumulative density function (ncdf)  logarithm = natural, data normalization = true,

!!! note
    By default, `MvDispEn` uses the method termed `mvDEii` in [1], which follows the original multivariate embedding approach of Ahmed & Mandic [2]. The `v1` method therefore returns a singular entropy estimate.

    If the `v2` method is selected (`Methodx=="v2"`), the main method outlined in [1] termed `mvDE` is applied. In this case, entropy is estimated using each combination of multivariate delay vectors with lengths 1:max(m), with each entropy value returned accordingly. See [1] for more info.


---

```
MDisp, RDE = MvDispEn(Data::AbstractArray{T,2} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, c::Int=3, Methodx::String="v1", Typex::String="NCDF", Norm::Bool=false, Logx::Real=exp(1))
```

Returns the multivariate dispersion entropy estimate (`MDisp`) for the M  multivariate data sequences in `Data` using the specified keyword arguments:

# Arguments:

`Data`    - Multivariate dataset, NxM matrix of N (>10) observations (rows) and M (cols) univariate data sequences

`m`       - Embedding Dimension, a vector of M positive integers

`tau`     - Time Delay, a vector of M positive integers

`c`       - Number of symbols in transform, an integer > 1 

`Methodx` - The method of multivariate dispersion entropy estimation as outlined in [1], either:

```
    * `"v1"` - employs the method consistent with the original multivariate embedding approach of Ahmed &
                Mandic [2], termed `mvDEii` in [1]. (default)
    * `"v2"` - employs the main method derived in [1],  termed `mvDE`.
```

`Typex`   - Type of data-to-symbolic sequence transform, one of the following:

```
            {`'linear'`, `'kmeans'`, `'ncdf'`, `'equal'`}
        See the `EntropyHub Guide` for more info on these transforms.
```

`Norm`    - Normalisation of `MDisp` and `RDE` values, a boolean:

```
            * [false]   no normalisation (default)
            * [true]    normalises w.r.t number of possible dispersion patterns (`c^m`).
```

`Logx`   - Logarithm base, a positive scalar 

# See also   `DispEn`, `DispEn2D`, `MvSampEn`, `MvFuzzEn`, `MvPermEn`, `MSEn`

# References:

```
[1] H Azami, A Fernández, J Escudero
      "Multivariate Multiscale Dispersion Entropy of Biomedical Times Series"
      Entropy 2019, 21, 913.

[2] Ahmed Mosabber Uddin, Danilo P. Mandic
      "Multivariate multiscale entropy: A tool for complexity
      analysis of multichannel data."
      Physical Review E 84.6 (2011): 061918.

[3] Mostafa Rostaghi and Hamed Azami,
       "Dispersion entropy: A measure for time-series analysis." 
       IEEE Signal Processing Letters 
       23.5 (2016): 610-614.

[4] Hamed Azami and Javier Escudero,
       "Amplitude-and fluctuation-based dispersion entropy." 
       Entropy 
       20.3 (2018): 210.

[5] Li Yuxing, Xiang Gao and Long Wang,
       "Reverse dispersion entropy: A new complexity measure for sensor signal." 
       Sensors 
       19.23 (2019): 5203.
```
