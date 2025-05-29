```
improper_explicit_imports(mod::Module, file=pathof(mod); strict=true, skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                          allow_internal_imports=true)
```

Attempts do detect various kinds of "improper" explicit imports taking place in `mod` and any submodules of `mod`.

Currently detects two classes of issues:

  * names which are explicitly imported but unused (stale)
  * names which are not public in `mod`

      * here, public means either exported or declared with the `public` keyword (requires Julia v1.11+)
      * one particularly egregious type of non-public import is when a name is imported from a module which does not even "own" that name. See the returned fields `importing_from_owns_name` and `importing_from_submodule_owns_name` for two variations on this.

The keyword argument `allow_internal_imports` determines whether or not "internal" explicit imports to other modules in the same package (or more generally, sharing the same `Base.moduleroot`) are reported here. If `allow_internal_imports=false`, then even such "internal" explicit imports will be returned.

The keyword argument `skip` is expected to be an iterator of `importing_from => parent` pairs, where names which are imported from `importing_from` but who have an ancestor which is `parent` are ignored. By default, imports from Base to names owned by Core are skipped.

This functionality is still in development, so the exact results may change in future non-breaking releases. Read on for the current outputs, what may change, and what will not change (without a breaking release of ExplicitImports.jl).

Returns a nested structure providing information about improper explicit imports to names in other modules. This information is structured as a collection of pairs, where the keys are the submodules of `mod` (including `mod` itself). Currently, the values are either `nothing` or a `Vector` of `NamedTuple`s with the following keys:

  * `name::Symbol`: the name being imported
  * `location::String`: the location the import takes place
  * `value::Any`: the which `name` points to in `mod`
  * `importing_from::Module`: the module the name is being imported from (e.g. in the example `using Foo.X: bar`, this would be `X`)
  * `whichmodule::Module`: the `Base.which` of the object
  * `public_import::Bool`: whether or not `name` is public or exported in `importing_from`. Checking if a name is marked `public` requires Julia v1.11+.
  * `importing_from_owns_name::Bool`: whether or not `importing_from` matches `whichmodule` and therefore is considered to directly "own" the name
  * `importing_from_submodule_owns_name::Bool`: whether or not `whichmodule` is a submodule of `importing_from`
  * `stale::Bool`: whether or not the explicitly imported name is used
  * `internal_import::Bool`: whether or not the import is "internal", meaning the module it was imported into and the module it was imported from share the same `Base.moduleroot`.

If `strict=true`, then returns `nothing` if `mod` could not be fully analyzed.

In non-breaking releases of ExplicitImports:

  * more columns may be added to these rows
  * additional rows may be returned which qualify as some other kind of "improper" access

However, the result will be a Tables.jl-compatible row-oriented table (for each module), with at least all of the same columns (or the value will be `nothing` if `strict=true` and the module could not be fully analyzed).

See also [`print_explicit_imports`](@ref) to easily compute and print these results, [`improper_explicit_imports_nonrecursive`](@ref) for a non-recursive version which ignores submodules, as well as [`check_no_stale_explicit_imports`](@ref), [`check_all_explicit_imports_via_owners`](@ref), and [`check_all_explicit_imports_are_public`](@ref) for specific regression-testing helpers.
