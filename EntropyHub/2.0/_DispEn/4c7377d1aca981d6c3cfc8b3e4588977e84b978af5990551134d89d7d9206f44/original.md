```
Dispx, RDE = DispEn(Sig)
```

Returns the dispersion entropy (`Dispx`) and the reverse dispersion entropy (`RDE`) estimated from the data sequence (`Sig`) using the default parameters: embedding dimension = 2, time delay = 1, symbols = 3, logarithm = natural, data transform = normalised cumulative density function (ncdf)

```
Dispx, RDE = DispEn(Sig::AbstractArray{T,1} where T<:Real; c::Int=3, m::Int=2, tau::Int=1, Typex::String="ncdf", Logx::Real=exp(1), Fluct::Bool=false, Norm::Bool=false, rho::Real=1)
```

Returns the dispersion entropy (`Dispx`) and the reverse dispersion entropy (`RDE`) estimated from the data sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer

`tau`   - Time Delay, a positive integer

`c`     - Number of symbols, an integer > 1

`Typex` - Type of data-to-symbolic sequence transform, one of the following:           {`"linear", "kmeans" ,"ncdf", "finesort", "equal"`}

```
      See the EntropyHub guide for more info on these transforms.
```

`Logx`  - Logarithm base, a positive scalar

`Fluct` - When Fluct == true, DispEn returns the fluctuation-based           Dispersion entropy.   [default: false]

`Norm`  - Normalisation of Dispx and RDE value:           [false]  no normalisation - default           [true]   normalises w.r.t number of possible dispersion patterns                     (c^m  or (2c -1)^m-1 if Fluct == true).

`rho`   - *If Typex == 'finesort', rho is the tuning parameter* (default: 1)

# See also `PermEn`, `SyDyEn`, `MSEn`

# References:

```
[1] Mostafa Rostaghi and Hamed Azami,
    "Dispersion entropy: A measure for time-series analysis." 
    IEEE Signal Processing Letters 
    23.5 (2016): 610-614.

[2] Hamed Azami and Javier Escudero,
    "Amplitude-and fluctuation-based dispersion entropy." 
    Entropy 
    20.3 (2018): 210.

[3] Li Yuxing, Xiang Gao and Long Wang,
    "Reverse dispersion entropy: A new complexity measure for 
    sensor signal." 
    Sensors 
    19.23 (2019): 5203.

[4] Wenlong Fu, et al.,
    "Fault diagnosis for rolling bearings based on fine-sorted 
    dispersion entropy and SVM optimized with mutation SCA-PSO."
    Entropy
    21.4 (2019): 404.
```
