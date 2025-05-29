```
url = pkg_docs_site(package::String; autoopen=true)
```

Attempt to find the URL of a package's documentation site by searching  through the local database established by previous calls to `add_pkg_docs`. If there is no entry in the database for the requested package, the  package repository URL is obtained instead via a call to `pkg_site`. If `autoopen` is `true` (default), then the URL is opened using the  default browser.

# Example

Assume that in some previous (or the current) Julia session the user has entered

```
julia> using PkgOnlineHelp

julia> add_pkg_docs("PSSFSS", "https://simonp0420.github.io/PSSFSS.jl/stable/")
```

Then in the same or a later Julia session:

```
julia> using PkgOnlineHelp

julia> pkg_docs_site("PSSFSS")
"https://simonp0420.github.io/PSSFSS.jl/stable/"
```

In addition, the site is opened in the user's default browser.
