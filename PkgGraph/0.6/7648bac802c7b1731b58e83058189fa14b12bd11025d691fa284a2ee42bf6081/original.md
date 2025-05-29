```
depgraph_web(pkgname, base_url = first(webapps); kw...)
```

Open the browser to an image of `pkgname`'s dependency graph.

See [`url`](@ref) for more on `base_url`. Keyword arguments are passed on to [`depgraph_as_dotstr`](@ref)
