```
echoAmplitudes(seq::MESequence, R1::AbstractFloat, R2::AbstractFloat, numStates=nothing)
```

calculates echo amplitudes for a given `MESequence` and given relaxation Rates R1, R2. Calculations are performed using the extended phase graph method. For simplicity instantaneous pulses are assumed. If `numStates=nothing` all dephasing states will be taken into account

# Arguments

  * `seq::MESequence` - pulse sequence
  * `R1::AbstractFloat` - R1 value to use (1/T1)
  * `R2::AbstractFloat` - R2 value to use (1/T2)
  * `numStates=nothing` - number of dephasing states to consider
