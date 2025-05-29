```
info(registry)
```

Show information about a registry, specifically its name, description and fields.

## Examples

{cell}

```julia
using FeatureRegistries: exampleregistry, info
registry = exampleregistry()
info(registry)
```
