```
Spectrum(c::CorrelationFunction, ps=[]; kwargs...)
```

[`CorrelationFunction`](@ref) `c` のフーリエ変換に対応する [`Spectrum`](@ref) のインスタンスを作成します。

# 例

```
julia> c = CorrelationFunction(a',a,de;steady_state=true)
⟨a′*a_0⟩

julia> S = Spectrum(c)
ℱ(⟨a′*a_0⟩)(ω)
```
