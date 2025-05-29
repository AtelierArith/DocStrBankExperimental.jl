```
setup_provider(s::Union{Symbol, AbstractString})
```

Perform any side-effects necessary to set up the given provider. For example, in IJulia, this causes the frontend to load the webio javascript bundle.
