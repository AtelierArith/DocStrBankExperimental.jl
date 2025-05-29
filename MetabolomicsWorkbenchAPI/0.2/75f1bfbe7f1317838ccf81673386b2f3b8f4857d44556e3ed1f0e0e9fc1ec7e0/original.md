```
check_mw(url::AbstractString) => String
```

Checks if Metabolomics Workbench server is responding properly. Returns the HTTP status code (`200` if successful) and prints a message.

# Example

```julia
julia> check_mw()
MetabolomicsWorkbench.org is alive.
200
```
