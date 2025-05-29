```
explicit_imports(mod::Module, file=pathof(mod); skip=(mod, Base, Core), strict=true)
```

Returns a nested structure providing information about explicit import statements one could make for each submodule of `mod`. This information is structured as a collection of pairs, where the keys are the submodules of `mod` (including `mod` itself), and the values are `NamedTuple`s, with at least the keys `name`, `source`, `exporters`, and `location`, showing which names are being used implicitly, which modules they were defined in, which modules they were exported from, and the location of those usages. Additional keys may be added to the `NamedTuple`'s in the future in non-breaking releases of ExplicitImports.jl.

## Arguments

  * `mod::Module`: the module to (recursively) analyze. Often this is a package.
  * `file=pathof(mod)`: this should be a path to the source code that contains the module `mod`.

      * if `mod` is the top-level module of a package, `pathof` will be unable to find the code, and a file must be passed which contains `mod` (either directly or indirectly through `include`s)
      * `mod` can be a submodule defined within `file`, but if two modules have the same name (e.g. `X.Y.X` and `X`), results may be inaccurate.

## Keyword arguments

  * `skip=(mod, Base, Core)`: any names coming from the listed modules (or any submodules thereof) will be skipped. Since `mod` is included by default, implicit imports of names exported from its own submodules will not count by default.
  * `strict=true`: when `strict` is set, results for a module will be `nothing` in the case that the analysis could not be performed accurately, due to e.g. dynamic `include` statements. When `strict=false`, results are returned in all cases, but may be inaccurate.

!!! note
    If `mod` is a package, we can detect the explicit_imports in the package extensions if those extensions are explicitly loaded before calling this function.

    For example, consider `PackageA` has a weak-dependency on `PackageB` and `PackageC` in the module `PkgBPkgCExt`

    ```julia-repl
    julia> using ExplicitImports, PackageA

    julia> explicit_imports(PackageA) # Only checks for explicit imports in PackageA and its submodules but not in `PkgBPkgCExt`
    ```

    To check for explicit imports in `PkgBPkgCExt`, you can do the following:

    ```julia-repl
    julia> using ExplicitImports, PackageA, PackageB, PackageC

    julia> explicit_imports(PackageA) # Now checks for explicit imports in PackageA and its submodules and also in `PkgBPkgCExt`
    ```


See also [`print_explicit_imports`](@ref) to easily compute and print these results, [`explicit_imports_nonrecursive`](@ref) for a non-recursive version which ignores submodules, and  [`check_no_implicit_imports`](@ref) for a version that throws errors, for regression testing.
