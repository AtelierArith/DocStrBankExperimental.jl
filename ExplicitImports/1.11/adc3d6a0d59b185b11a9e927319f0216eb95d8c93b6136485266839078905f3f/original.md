```
check_all_explicit_imports_are_public(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                      skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,),
                                      allow_internal_imports=true)
```

Checks that neither `mod` nor any of its submodules has imports to names which are non-public (i.e. not exported, nor declared public on Julia 1.11+) throwing an `NonPublicExplicitImportsException` if so, and returning `nothing` otherwise.

This can be used in a package's tests, e.g.

```julia
@test check_all_explicit_imports_are_public(MyPackage) === nothing
```

## Allowing some non-public explicit imports

The `skip` keyword argument can be passed to allow non-public imports from some modules (and their submodules). One pases a tuple of `importing_from => pub` pairs, allowing cases in which a name is being imported from the module `importing_from`, but is public in the module `pub`. By default, `skip` is set to `(Base => Core,)`, meaning that names which are imported from Base but are public in Core are not flagged.

For example:

```julia
@test check_all_explicit_imports_are_public(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

would allow explicitly importing names which are public in PrettyTables from DataFrames.

If `ignore` is supplied, it should be a tuple of `Symbol`s, representing names that are allowed to be imported from modules in which they are not public. For example,

```julia
@test check_all_explicit_imports_are_public(MyPackage; ignore=(:DataFrame,)) === nothing
```

would check there were no non-public explicit imports besides that of the name `DataFrame`.

## non-fully-analyzable modules do not cause exceptions

Note that if a module is not fully analyzable (e.g. it has dynamic `include` calls), explicit imports of non-public names which could not be analyzed will be missed. Unlike [`check_no_stale_explicit_imports`](@ref) and [`check_no_implicit_imports`](@ref), this function will *not* throw an `UnanalyzableModuleException` in such cases.

See also: [`improper_explicit_imports`](@ref) for programmatic access to such imports and the meaning of the keyword argument `allow_internal_imports`, and [`check_all_explicit_imports_via_owners`] for a weaker version of this check. Note that while `improper_explicit_imports` may increase in scope and report other kinds of improper accesses, `check_all_explicit_imports_are_public` will not.
