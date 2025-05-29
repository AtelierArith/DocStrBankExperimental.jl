```
explicit_imports_nonrecursive(mod::Module, file=pathof(mod); skip=(mod, Base, Core), strict=true)
```

A non-recursive version of [`explicit_imports`](@ref), meaning it only analyzes the module `mod` itself, not any of its submodules; see that function for details.

## Keyword arguments

  * `skip=(mod, Base, Core)`: any names coming from the listed modules (or any submodules thereof) will be skipped. Since `mod` is included by default, implicit imports of names exported from its own submodules will not count by default.
  * `strict=true`: when `strict=true`, results will be `nothing` in the case that the analysis could not be performed accurately, due to e.g. dynamic `include` statements. When `strict=false`, results are returned in all cases, but may be inaccurate.
