```
@docs PackageName
```

Retrieve the URL of the package's documentation site if previously recorded via a call to `add_pkg_docs` or to the package's repository otherwise.  Open the URL in the user's  default browser.

# Examples

```
julia> using PkgOnlineHelp

julia> @docs StaticArrays
"https://github.com/JuliaArrays/StaticArrays.jl.git"
```

The `StaticArrays` repo site is returned and opened in the browser.  In this example the user had not previously entered the actual documentation site via a prior call to `add_pkg_docs`. The repo site was found by searching through all Julia registries in `DEPOT_PATH`. 

`@docs` can also be used to access unregistered packages or even arbitrary web sites. Suppose you wish to have rapid access to the portion of the Julia documentation discussing macros.  Then you would (one time only) enter the following at the Julia prompt:

```julia
julia> add_pkg_docs("macros", "https://docs.julialang.org/en/v1/manual/metaprogramming/#man-macros")
```

Later in this Julia session, or in any future session, the site can be quickly opened by entering

```julia
julia> @docs macros
```

Of course, this example assumes that `using PkgOnlineHelp` has already been entered.   For convenience, you may wish to include this statement in your `startup.jl` file.

# See Also

`add_pkg_docs`, `remove_pkg_docs`, `list_pkg_docs`, `pkg_site`
