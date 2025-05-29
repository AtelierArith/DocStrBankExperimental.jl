```
gensave_snapshot!(io, model, T, [N=1])
gensave_snapshot!(filename, model, T, [N=1])
```

generate and write `N` snapshots into `io` or `filename`.

# Arguments

  * `io::IO` : output stream where snapshots will be written
  * `filename::String` : the name of file where snapshots will be written
  * `model::Model` : model to be simulated
  * `T::Real` : temperature
  * `N::Integer=1` : the number of snapshots to be generated
  * `MCS::Integer=1` : the number of Monte Carlo steps followed by snapshot generation
  * `sep::String=" "` : field separator of snapshot
