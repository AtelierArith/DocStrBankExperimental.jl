```
analyze(m::Module; kwargs...) -> PackageV1
```

If you want to analyze a package which is already loaded in the current session, you can simply call `analyze`, which uses `pkgdir` to determine its source code:

```julia
julia> using DataFrames

julia> analyze(DataFrames)
PackageV1 DataFrames:
  * repo:
  * uuid: a93c6f00-e57d-5684-b7b6-d8193f3e46c0
  * version: 0.0.0
  * is reachable: true
  * tree hash: db2a9cb664fcea7836da4b414c3278d71dd602d2
  * Julia code in `src`: 15628 lines
  * Julia code in `test`: 21089 lines (57.4% of `test` + `src`)
  * documention in `docs`: 6270 lines (28.6% of `docs` + `src`)
  * documention in README: 21 lines
  * has license(s) in file: MIT
    * filename: LICENSE.md
    * OSI approved: true
  * has `docs/make.jl`: true
  * has `test/runtests.jl`: true
  * has continuous integration: true
    * GitHub Actions
```
