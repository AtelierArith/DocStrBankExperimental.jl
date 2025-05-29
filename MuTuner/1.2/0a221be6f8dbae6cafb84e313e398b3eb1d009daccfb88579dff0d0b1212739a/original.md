```
save(μtuner::MuTunerLogger{T,S}, filename::String, filepath::String = "")
```

Replay the chemical potential tuner to its current state, writing the time series of relevant values to a space-delimited CSV file.
