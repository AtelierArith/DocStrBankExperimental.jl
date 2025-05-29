```
FlashResult(compositions,fractions,volumes,data::FlashData)
FlashResult(model,p,T,z,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(model,p,T,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(model,p,T,z;phase = :unknown)
FlashResult(p,T,z,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(p,T,compositions,fractions,volumes,g = nothing;sort = true)
FlashResult(flash::FlashResult,g = nothing;sort = true)
```

Structure used to contain the result of a flash. Contains a list of molar compositions, a list of molar amounts per phase, a list of molar volumes and an auxiliary struct, `FlashData`, containing the pressure, temperature and reduced gibbs energy. when an `EoSModel` is used as an input for a `FlashResult`, the reduced molar gibbs energy (g = g/NRT) is calculated, if not provided. By default, the phases are sorted by volume, this can be changed by passing the keyword argument `sort = false` `FlashResult(model,p,T,z;phase)` constructs a single phase `FlashResult`. If the bulk composition `z` is provided, it will be used to scale the fractions, forcing `sum(fractions) == sum(z)`
