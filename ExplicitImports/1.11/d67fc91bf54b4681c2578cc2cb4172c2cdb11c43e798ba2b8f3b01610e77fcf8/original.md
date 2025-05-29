```
improper_explicit_imports_nonrecursive(mod::Module, file=pathof(mod); strict=true, skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                                       allow_internal_imports=true)
```

A non-recursive version of [`improper_explicit_imports`](@ref), meaning it only analyzes the module `mod` itself, not any of its submodules; see that function for details, including important caveats about stability (outputs may grow in future non-breaking releases of ExplicitImports!).

If `strict=true`, then returns `nothing` if `mod` could not be fully analyzed.
