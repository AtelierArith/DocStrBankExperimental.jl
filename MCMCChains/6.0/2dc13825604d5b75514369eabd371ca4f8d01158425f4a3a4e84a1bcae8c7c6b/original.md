```
set_section(chains::Chains, namemap)
```

Create a new `Chains` object from `chains` with the provided `namemap` mapping of parameter names.

Both chains share the same underlying data. Any parameters in the chain that are unassigned will be placed into the `:parameters` section.
