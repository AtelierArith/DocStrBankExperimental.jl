```
print_explicit_imports([io::IO=stdout,] mod::Module, file=pathof(mod); skip=(mod, Base, Core),
                       warn_implicit_imports=true,
                       warn_improper_explicit_imports=true,
                       warn_improper_qualified_accesses=true,
                       report_non_public=VERSION >= v"1.11-",
                        strict=true)
```

Runs [`explicit_imports`](@ref) and prints the results, along with those of [`improper_explicit_imports`](@ref) and [`improper_qualified_accesses`](@ref).

Note that the particular printing may change in future non-breaking releases of ExplicitImports.

## Keyword arguments

  * `skip=(mod, Base, Core)`: any names coming from the listed modules (or any submodules thereof) will be skipped. Since `mod` is included by default, implicit imports of names exported from its own submodules will not count by default.
  * `warn_improper_explicit_imports=true`: if set, this function will also print information about any "improper" imports of names from other modules.
  * `warn_improper_qualified_accesses=true`: if set, this function will also print information about any "improper" qualified accesses to names from other modules.
  * `strict=true`: when `strict` is set, a module will be noted as unanalyzable in the case that the analysis could not be performed accurately, due to e.g. dynamic `include` statements. When `strict=false`, results are returned in all cases, but may be inaccurate.
  * `show_locations=false`: whether or not to print locations of where the names are being used.
  * `separate_lines=false`: whether or not to print each `using` statement on a separate line. Automatically occurs when `show_locations=true`.
  * `linewidth=80`: format into lines of up to this length. Set to 0 to indicate one name should be printed per line.
  * `report_non_public=VERSION >= v"1.11-"`: report if there are accesses or imports of non-public names (that is, names that are not exported nor marked public). By default, only activates on Julia v1.11+.
  * `allow_internal_accesses=true`: if false, reports non-owning or non-public qualified accesses to other modules in the same package
  * `allow_internal_imports=true`: if false, reports non-owning or non-public explicit imports from other modules in the same package

See also [`check_no_implicit_imports`](@ref), [`check_no_stale_explicit_imports`](@ref), [`check_all_qualified_accesses_via_owners`](@ref), and [`check_all_explicit_imports_via_owners`](@ref).
