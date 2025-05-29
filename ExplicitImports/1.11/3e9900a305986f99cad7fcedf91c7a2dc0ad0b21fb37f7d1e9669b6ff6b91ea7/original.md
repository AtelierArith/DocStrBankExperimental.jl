```
check_all_qualified_accesses_via_owners(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                        require_submodule_access=false,
                                        skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,
                                                                       Compat => Base,
                                                                       Compat => Core),
                                        allow_internal_accesses=true)
```

Checks that neither `mod` nor any of its submodules has accesses to names via modules other than their owner as determined by `Base.which` (unless the name is public or exported in that module), throwing an `QualifiedAccessesFromNonOwnerException` if so, and returning `nothing` otherwise.

This can be used in a package's tests, e.g.

```julia
@test check_all_qualified_accesses_via_owners(MyPackage) === nothing
```

## Allowing some qualified accesses via non-owner modules

The `skip` keyword argument can be passed to allow non-owning accesses via some modules (and their submodules). One pases a tuple of `accessing_from => parent` pairs, allowing cases in which a name is being imported from the module `accessing_from`, but is owned by the module `parent`. By default, `skip` is set to `(Base => Core,)`, meaning that names which are accessed from Base but are owned by Core are not flagged.

For example:

```julia
@test check_all_qualified_accesses_via_owners(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

would allow explicitly accessing names which are owned by PrettyTables from DataFrames.

If `ignore` is supplied, it should be a tuple of `Symbol`s, representing names that are allowed to be accessed from non-owner modules. For example,

```julia
@test check_all_qualified_accesses_via_owners(MyPackage; ignore=(:DataFrame,)) === nothing
```

would check there were no qualified accesses from non-owner modules besides that of the name `DataFrame`.

If `require_submodule_access=true`, then an error will be thrown if the name is accessed by a non-owner module even if it is accessed by a parent module of the owner module. For example, in June 2024, `JSON.parse` is actually defined in the submodule `JSON.Parser` and is not declared public inside `JSON`, but the name is present within the module `JSON`. If `require_submodule_access=false`, the default, in this scenario the access `JSON.parse` will not trigger an error, since the name is being accessed by a parent of the owner. If `require_submodule_access=false`, then accessing the function as `JSON.Parser.parse` will be required to avoid an error.

See also: [`improper_qualified_accesses`](@ref) for programmatic access and the meaning of the keyword argument `allow_internal_accesses`, and [`check_all_qualified_accesses_are_public`](@ref) for a stricter version of this check. Note that while `improper_qualified_accesses` may increase in scope and report other kinds of improper accesses, `check_all_qualified_accesses_via_owners` will not.
