```
dose(spec::Spectrum, def=missing)
dose(props::Dict{Symbol, Any}, def=missing)
```

プローブの線量は nA⋅s であり、spec[:LiveTime]⋅spec[:ProbeCurrent] に等しいです。
