```
struct FilteredRK4TimeStepper{T,Tf} <: AbstractTimeStepper{T}
```

スペクトルフィルタリングを伴う4次のルンゲ・クッタタイムステッパーです。 [`RK4TimeStepper`](@ref)を参照してください。
