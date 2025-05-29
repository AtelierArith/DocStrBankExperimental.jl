```
struct FilteredForwardEulerTimeStepper{T,Tf} <: AbstractTimeStepper{T}
```

スペクトルフィルタリングを伴う前方オイラータイムステッパーです。 [`ForwardEulerTimeStepper`](@ref)を参照してください。
