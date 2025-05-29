```
check_no_implicit_imports(mod::Module, file=pathof(mod); skip=(mod, Base, Core), ignore::Tuple=(),
                          allow_unanalyzable::Tuple=())
```

Checks that neither `mod` nor any of its submodules is relying on implicit imports, throwing an `ImplicitImportsException` if so, and returning `nothing` otherwise.

This function can be used in a package's tests, e.g.

```julia
@test check_no_implicit_imports(MyPackage) === nothing
```

## Allowing some submodules to be unanalyzable

Pass `allow_unanalyzable` as a tuple of submodules which are allowed to be unanalyzable. Any other submodules found to be unanalyzable will result in an `UnanalyzableModuleException` being thrown.

These unanalyzable submodules can alternatively be included in `ignore`.

## Allowing some implicit imports

The `skip` keyword argument can be passed to allow implicit imports from some modules (and their submodules). By default, `skip` is set to `(Base, Core)`. For example:

```julia
@test check_no_implicit_imports(MyPackage; skip=(Base, Core, DataFrames)) === nothing
```

would verify there are no implicit imports from modules other than Base, Core, and DataFrames.

Additionally, the keyword `ignore` can be passed to represent a tuple of items to ignore. These can be:

  * modules. Any submodule of `mod` matching an element of `ignore` is skipped. This can be used to allow the usage of implicit imports in some submodule of your package.
  * symbols: any implicit import of a name matching an element of `ignore` is ignored (does not throw)
  * `symbol => module` pairs. Any implicit import of a name matching that symbol from a module matching the module is ignored.

One can mix and match between these type of ignored elements. For example:

```julia
@test check_no_implicit_imports(MyPackage; ignore=(:DataFrame => DataFrames, :ByRow, MySubModule)) === nothing
```

This would:

1. Ignore any implicit import of `DataFrame` from DataFrames
2. Ignore any implicit import of the name `ByRow` from any module.
3. Ignore any implicit imports present in `MyPackage`'s submodule `MySubModule`

but verify there are no other implicit imports.
