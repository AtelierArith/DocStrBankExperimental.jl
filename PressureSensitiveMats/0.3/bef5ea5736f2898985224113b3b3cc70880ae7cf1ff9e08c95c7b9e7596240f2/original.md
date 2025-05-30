```
occupancy_detection(x::AbstractVector; kwargs)
```

Implements signle sensor simple occupancy detection from Long-Term Sleep Assessment by  Unobtrusive Pressure Sensor Arrays - 2018, Soleimani.

# Arguments

  * `β=350` : Average value of a sensor from an empty bed.
  * `m=300` : Minimum number of samples to be declared an occupancy.
  * `n=4` : Sensitivity parameter
