```
   Phas = PhasEn(Sig)
```

Returns the phase entropy (`Phas`) estimate of the data sequence (`Sig`)    using the default parameters:     angular partitions = 4, time delay = 1, logarithm = natural,

```
   Phas = PhasEn(Sig::AbstractArray{T,1} where T<:Real; K::Int=4, tau::Int=1, Logx::Real=exp(1), Norm::Bool=true, Plotx::Bool=false)
```

Returns the phase entropy (`Phas`) estimate of the data sequence (`Sig`)      using the specified 'keyword' arguments:

# Arguments:

`K`     - Angular partitions (coarse graining), an integer > 1  

```
           *Note: Division of partitions begins along the positive x-axis. As this point is somewhat arbitrary, it is
            recommended to use even-numbered (preferably multiples of 4) partitions for sake of symmetry.
```

`tau`   - Time Delay, a positive integer    

`Logx`  - Logarithm base, a positive scalar 

`Norm`  - Normalisation of `Phas` value:    

```
         [false]  no normalisation
         [true]   normalises w.r.t. the number of partitions Log(`K`)
```

`Plotx` - When `Plotx` == true, returns Poincaré plot (default: false)  

# See also `SampEn`, `ApEn`, `GridEn`, `MSEn`, `SlopEn`, `CoSiEn`, `BubbEn`

# References:

```
   [1] Ashish Rohila and Ambalika Sharma,
       "Phase entropy: a new complexity measure for heart rate
       variability." 
       Physiological measurement
       40.10 (2019): 105006.
```
