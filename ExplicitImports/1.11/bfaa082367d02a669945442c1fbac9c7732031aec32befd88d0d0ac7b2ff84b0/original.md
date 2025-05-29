```
check_all_explicit_imports_via_owners(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                      require_submodule_import=false,
                                      skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core)),
                                      allow_internal_imports=true)
```

Checks that neither `mod` nor any of its submodules has imports to names via modules other than their owner as determined by `Base.which` (unless the name is public or exported in that module), throwing an `ExplicitImportsFromNonOwnerException` if so, and returning `nothing` otherwise.

This can be used in a package's tests, e.g.

```julia
@test check_all_explicit_imports_via_owners(MyPackage) === nothing
```

## Allowing some explicit imports via non-owner modules

The `skip` keyword argument can be passed to allow non-owning imports from some modules (and their submodules). One pases a tuple of `importing_from => parent` pairs, allowing cases in which a name is being imported from the module `importing_from`, but is owned by the module `parent`. By default, `skip` is set to `(Base => Core,)`, meaning that names which are imported from Base but are owned by Core are not flagged.

For example:

```julia
@test check_all_explicit_imports_are_public(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

would allow explicitly importing names which are owned by PrettyTables from DataFrames.

If `ignore` is supplied, it should be a tuple of `Symbol`s, representing names that are allowed to be accessed from non-owner modules. For example,

```julia
@test check_all_explicit_imports_via_owners(MyPackage; ignore=(:DataFrame,)) === nothing
```

would check there were no explicit imports from non-owner modules besides that of the name `DataFrame`.

## `require_submodule_import`

If `require_submodule_import=true`, then an error will be thrown if the name is imported from a non-owner module even if it is imported from a parent module of the owner module. For example, in June 2024, `JSON.parse` is actually defined in the submodule `JSON.Parser` and is not declared public inside `JSON`, but the name is present within the module `JSON`. If `require_submodule_import=false`, the default, in this scenario the access `using JSON: parse` will not trigger an error, since the name is being accessed by a parent of the owner. If `require_submodule_import=false`, then accessing the function as `using JSON.Parser: parse` will be required to avoid an error.

## non-fully-analyzable modules do not cause exceptions

Note that if a module is not fully analyzable (e.g. it has dynamic `include` calls), explicit imports of non-public names which could not be analyzed will be missed. Unlike [`check_no_stale_explicit_imports`](@ref) and [`check_no_implicit_imports`](@ref), this function will *not* throw an `UnanalyzableModuleException` in such cases.

See also: [`improper_explicit_imports`](@ref) for programmatic access to such imports and the meaning of the keyword argument `allow_internal_imports`, and [`check_all_explicit_imports_are_public`](@ref) for a stricter version of this check. Note that while `improper_explicit_imports` may increase in scope and report other kinds of improper accesses, `check_all_explicit_imports_via_owners` will not.
