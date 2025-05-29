```
improper_qualified_accesses(mod::Module, file=pathof(mod); skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                            allow_internal_accesses=true)
```

Attempts do detect various kinds of "improper" qualified accesses taking place in `mod` and any submodules of `mod`.

Currently, only detects cases in which the name is being accessed from a module `mod` for which:

  * `name` is not exported from `mod`
  * or `name` is not declared public in `mod` (requires Julia v1.11+)
  * or `name` is "self-qualified": i.e. in the module `Foo`, `Foo.name` is being accessed.

The keyword argument `allow_internal_accesses` determines whether or not "internal" qualified accesses to other modules in the same package (or more generally, sharing the same `Base.moduleroot`) are reported here. If `allow_internal_accesses=false`, then even such "internal" qualified accesses will be returned. Note self-qualified accesses are reported regardless of the setting of `allow_internal_accesses`.

The keyword argument `skip` is expected to be an iterator of `accessing_from => parent` pairs, where names which are accessed from `accessing_from` but who have an ancestor `parent` are ignored. By default, accesses from Base to names owned by Core are skipped.

This functionality is still in development, so the exact results may change in future non-breaking releases. Read on for the current outputs, what may change, and what will not change (without a breaking release of ExplicitImports.jl).

Returns a nested structure providing information about improper accesses to names in other modules. This information is structured as a collection of pairs, where the keys are the submodules of `mod` (including `mod` itself). Currently, the values are a `Vector` of `NamedTuple`s with the following keys:

  * `name::Symbol`: the name being accessed
  * `location::String`: the location the access takes place
  * `value::Any`: the which `name` points to in `mod`
  * `accessing_from::Module`: the module the name is being accessed from (e.g. `Module.name`)
  * `whichmodule::Module`: the `Base.which` of the object
  * `public_access::Bool`: whether or not `name` is public or exported in `accessing_from`. Checking if a name is marked `public` requires Julia v1.11+.
  * `accessing_from_owns_name::Bool`: whether or not `accessing_from` matches `whichmodule` and therefore is considered to directly "own" the name
  * `accessing_from_submodule_owns_name::Bool`: whether or not `whichmodule` is a submodule of `accessing_from`
  * `internal_access::Bool`: whether or not the access is "internal", meaning the module it was accessed in and the module it was accessed from share the same `Base.moduleroot`.
  * `self_qualified::Bool`: whether or not the access is "self-qualified", meaning the module it was accessed in and the module it is accessed from are the same module.

In non-breaking releases of ExplicitImports:

  * more columns may be added to these rows
  * additional rows may be returned which qualify as some other kind of "improper" access

However, the result will be a Tables.jl-compatible row-oriented table (for each module), with at least all of the same columns.

See also [`print_explicit_imports`](@ref) to easily compute and print these results, [`improper_qualified_accesses_nonrecursive`](@ref) for a non-recursive version which ignores submodules, and the `check_` functions  [`check_all_qualified_accesses_via_owners`](@ref) and [`check_all_explicit_imports_are_public`](@ref) for versions that throws errors, for regression testing.

## Example

```jldoctest
julia> using ExplicitImports

julia> example_path = pkgdir(ExplicitImports, "examples", "qualified.jl");

julia> print(read(example_path, String))
module MyMod
using LinearAlgebra
# sum is in `Base`, so we shouldn't access it from LinearAlgebra:
n = LinearAlgebra.sum([1, 2, 3])
end

julia> include(example_path);

julia> row = improper_qualified_accesses(MyMod, example_path)[1][2][1];

julia> (; row.name, row.accessing_from, row.whichmodule)
(name = :sum, accessing_from = LinearAlgebra, whichmodule = Base)
```
