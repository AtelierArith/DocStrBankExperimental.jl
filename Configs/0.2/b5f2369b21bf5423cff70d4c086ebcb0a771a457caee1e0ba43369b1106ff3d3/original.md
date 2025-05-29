```
initconfig(; <keyword arguments>)
```

Optionally override the configs environment.

Automatically called on first [`getconfig`](@ref), [`hasconfig`](@ref) or [`setconfig!`](@ref)

Can only be called once.

Alternatively, set the corresponding `ENV` variables `DEPLOYMENT_KEY` or `CONFIGS_DIRECTORY` to preference

## Arguments

  * `deployment_key::String`: The `ENV` key that defines the intended deployment (eg. production, staging, etc.)

Default: `DEPLOYMENT`

  * `configs_directory::String`: The directory containing config definitions

May be relative to project root or absolute   Default: `configs`
