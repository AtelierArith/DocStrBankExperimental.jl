```
check_no_self_qualified_accesses(mod::Module, file=pathof(mod);
                                ignore::Tuple=())
```

Checks that neither `mod` nor any of its submodules has self-qualified accesses, throwing an `SelfQualifiedAccessException` if so, and returning `nothing` otherwise.

This can be used in a package's tests, e.g.

```julia
@test check_no_self_qualified_accesses(MyPackage) === nothing
```

## Allowing some self-qualified accesses

If `ignore` is supplied, it should be a tuple of `Symbol`s, representing names that are allowed to be self-qualified. For example,

```julia
@test check_no_self_qualified_accesses(MyPackage; ignore=(:foo,)) === nothing
```

would check there were no self-qualified accesses besides that of the name `foo`.

## non-fully-analyzable modules do not cause exceptions

Note that if a module is not fully analyzable (e.g. it has dynamic `include` calls), qualified accesess of non-public names which could not be analyzed will be missed. Unlike [`check_no_stale_explicit_imports`](@ref) and [`check_no_implicit_imports`](@ref), this function will *not* throw an `UnanalyzableModuleException` in such cases.

See also: [`improper_qualified_accesses`](@ref) for programmatic access to the same information. Note that while `improper_qualified_accesses` may increase in scope and report other kinds of improper accesses, `check_all_qualified_accesses_are_public` will not.
