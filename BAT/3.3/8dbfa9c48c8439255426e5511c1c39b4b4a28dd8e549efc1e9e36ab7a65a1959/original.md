```
struct CuhreIntegration <: IntegrationAlgorithm
```

CuhreIntegration integration algorithm.

Constructors:

  * `CuhreIntegration(; fields...)`

Fields:

  * `trafo::BAT.AbstractTransformTarget`: Default: PriorToUniform()
  * `rtol::Float64`: Default: ext_default(pkgext(Val(:Cuba)), Val(:RTOL))
  * `atol::Float64`: Default: ext_default(pkgext(Val(:Cuba)), Val(:ATOL))
  * `minevals::Int64`: Default: ext_default(pkgext(Val(:Cuba)), Val(:MINEVALS))
  * `maxevals::Int64`: Default: ext_default(pkgext(Val(:Cuba)), Val(:MAXEVALS))
  * `key::Int64`: Default: ext_default(pkgext(Val(:Cuba)), Val(:KEY))
  * `nthreads::Int64`: Default: Base.Threads.nthreads()
  * `strict::Bool`: Default: true

!!! note
    This functionality is only available when the [Cuba](https://github.com/giordano/Cuba.jl) package is loaded (e.g. via `import CUBA`).

