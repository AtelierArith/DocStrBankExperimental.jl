```
occupancy_detection(x::AbstractMatrix; kwargs)
```

Implements simple occupancy detection from Long-Term Sleep Assessment by Unobtrusive Pressure Sensor Arrays - 2018, Soleimani.

# Arguments

  * `max_dist=false` : Use breathing availability signal from the maximum distance method.
  * `β=25000` : Average value of the sum of all sensors from an empty bed.
  * `m=300` : Minimum number of samples to be declared an occupancy.
  * `n=4` : Sensitivity parameter
