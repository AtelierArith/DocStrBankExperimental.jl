```
@usingany pkg
@usingany pkg1, pkg2, ... 
@usingany pkg: fn
@usingany pkg: fn, @mcr, ... 
@usingany kwarg = true [pkg...]
```

Makes package(s) available, if they are not already, and loads them with `using` keyword. 

  * If a package is available in an environment in `LOAD_PATH`, that's OK.
  * If a package is available in a shared environment, this environment will be pushed into `LOAD_PATH`.
  * Otherwise if package(s) can be installed, you will be prompted to select an environment to install each package.
  * If the package is not listed in any registry, an error will be thrown.

The macro can be called with keyword arguments:

  * `update_pkg::Bool`: if set to `true`, first updates the package(s) to be imported by the macro
  * `update_env::Bool`: first update the shared environments currently in the `LOAD_PATH`
  * `update_all::Bool`: first update ALL shared environments as well as the current project

If Julia version supports versioned manifests, on any updates a versioned manifest will be created in each updated env. See also [`make_current_mnf`](@ref) and [`update`](@ref).

If `update_all` or `update_env` kwarg is set, `@usingany` can be called without specifying any package(s) for import.  If `update_pkg` kwarg is set, package(s) to import must be specified.

This macro is exported.

# Examples

```julia-repl
julia> @usingany Foo, Bar
julia> @usingany Baz: quux
julia> @usingany update_all = true
julia> @usingany update_pkg = true Qux
```
