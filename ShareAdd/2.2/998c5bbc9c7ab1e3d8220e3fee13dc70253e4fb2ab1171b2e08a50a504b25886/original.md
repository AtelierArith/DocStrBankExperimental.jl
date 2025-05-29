```
make_importable(pkg::AbstractString)
make_importable(pkgs::AbstractVector{<:AbstractString})
make_importable(pkg1, pkg2, ...)
make_importable(::Nothing) => :success
```

Checks  packages (by name only, UUIDs not supported!), prompts to install packages which are not in any shared environment,  and adds relevant shared environments to `LOAD_PATH`.

`make_importable` is used internally by `@usingany`, but it can be used separately e.g.  if you e.g. want to import a package via `import` statement instead of `using`.

Returns `:success` if the operation was successful, and `nothing` if the user selected "Quit. Do Nothing." on any of the prompts.

Throws an error on unavailable packages.

# Examples

```julia-repl
julia> using ShareAdd
julia> make_importable("Foo")
:success
julia> import Foo 

julia> using ShareAdd
julia> make_importable("Foo")
:success
julia> using Foo: bazaar as baz  # @usingany Foo: bazaar as baz is not a supported syntax
```

This function is public, not exported.
