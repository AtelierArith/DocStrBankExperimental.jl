```
updatecheck_settings(; kwargs...)
```

Edits preferences applied to checking for update on the startup of `PackageMaker`.

`PackageMaker` checks regularly whether a new version of it became avaliable.  `updatecheck_settings` function is one of the ways to define how often the checks are done etc. You may also call it without arguments to display current settings.

# kwargs

  * `enabled::Bool`: Default is `true`
  * `default_frequency::Int`: How often the check is performed by default, in days. Default is 7,
  * `next_check::Int`: Delay in days till the next check from today. Default is `default_frequency`, and will be reset to default after the next check
  * `skip::Bool`: Skip this version. Default is `false`

# Examples

```julia-repl

julia> PackageMaker.updatecheck_settings(; enabled=false) # don't bother me again

julia> PackageMaker.updatecheck_settings(; skip=true) # I might update to this version myself

julia> PackageMaker.updatecheck_settings(; next_check=365*100) # Let's see then
```

This function is public, not exported. Therefore call it as `PackageMaker.updatecheck_settings(;kwargs...)`
