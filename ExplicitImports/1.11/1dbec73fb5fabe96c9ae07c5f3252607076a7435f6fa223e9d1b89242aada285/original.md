```
check_no_stale_explicit_imports(mod::Module, file=pathof(mod); ignore::Tuple=(), allow_unanalyzable::Tuple=())
```

Checks that neither `mod` nor any of its submodules has stale (unused) explicit imports, throwing an `StaleImportsException` if so, and returning `nothing` otherwise.

This can be used in a package's tests, e.g.

```julia
@test check_no_stale_explicit_imports(MyPackage) === nothing
```

## Allowing some submodules to be unanalyzable

Pass `allow_unanalyzable` as a tuple of submodules which are allowed to be unanalyzable. Any other submodules found to be unanalyzable will result in an `UnanalyzableModuleException` being thrown.

## Allowing some stale explicit imports

If `ignore` is supplied, it should be a tuple of `Symbol`s, representing names that are allowed to be stale explicit imports. For example,

```julia
@test check_no_stale_explicit_imports(MyPackage; ignore=(:DataFrame,)) === nothing
```

would check there were no stale explicit imports besides that of the name `DataFrame`.
