```
url = pkg_site(pkgname::AbstractString; autoopen=true)
```

Attempt to find the URL of a package's home repository, by searching through the  registries in `DEPOT_PATH`.  If `autoopen` is `true` (default), then open the URL using the default browser.

# Example

```jldoctest
julia> pkg_site("StaticArrays")
"https://github.com/JuliaArrays/StaticArrays.jl.git"
```

In this example the web site is also opened in the user's browser.
