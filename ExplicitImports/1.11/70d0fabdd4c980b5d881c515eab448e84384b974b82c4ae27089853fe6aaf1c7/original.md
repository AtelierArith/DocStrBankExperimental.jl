```
check_all_qualified_accesses_are_public(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                        skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,),
                                        allow_internal_accesses=true)
```

Checks that neither `mod` nor any of its submodules has qualified accesses to names which are non-public (i.e. not exported, nor declared public on Julia 1.11+) throwing an `NonPublicQualifiedAccessException` if so, and returning `nothing` otherwise.

This can be used in a package's tests, e.g.

```julia
@test check_all_qualified_accesses_are_public(MyPackage) === nothing
```

## Allowing some non-public qualified accesses

The `skip` keyword argument can be passed to allow non-public qualified accesses from some modules (and their submodules). One pases a tuple of `accessing_from => pub` pairs, allowing cases in which a name is being accessed from the module `accessing_from`, but is public in the module `pub`. By default, `skip` is set to `(Base => Core,)`, meaning that names which are accessed from Base but are public in Core are not flagged.

For example:

```julia
@test check_all_qualified_accesses_are_public(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

would allow accessing names which are public in PrettyTables from DataFrames.

If `ignore` is supplied, it should be a tuple of `Symbol`s, representing names that are allowed to be accessed from modules in which they are not public. For example,

```julia
@test check_all_qualified_accesses_are_public(MyPackage; ignore=(:DataFrame,)) === nothing
```

would check there were no non-public qualified accesses besides that of the name `DataFrame`.

## non-fully-analyzable modules do not cause exceptions

Note that if a module is not fully analyzable (e.g. it has dynamic `include` calls), qualified accesess of non-public names which could not be analyzed will be missed. Unlike [`check_no_stale_explicit_imports`](@ref) and [`check_no_implicit_imports`](@ref), this function will *not* throw an `UnanalyzableModuleException` in such cases.

See also: [`improper_qualified_accesses`](@ref) for programmatic access and the meaning of the keyword argument `allow_internal_accesses`, and [`check_all_qualified_accesses_via_owners`] for a weaker version of this check. Note that while `improper_qualified_accesses` may increase in scope and report other kinds of improper accesses, `check_all_qualified_accesses_are_public` will not.
