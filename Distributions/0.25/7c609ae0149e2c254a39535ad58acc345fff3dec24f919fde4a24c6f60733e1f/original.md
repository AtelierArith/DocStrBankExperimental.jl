```
sampler(d::Distribution) -> Sampleable
sampler(s::Sampleable) -> s
```

Samplers can often rely on pre-computed quantities (that are not parameters themselves) to improve efficiency. If such a sampler exists, it can be provided with this `sampler` method, which would be used for batch sampling. The general fallback is `sampler(d::Distribution) = d`.
