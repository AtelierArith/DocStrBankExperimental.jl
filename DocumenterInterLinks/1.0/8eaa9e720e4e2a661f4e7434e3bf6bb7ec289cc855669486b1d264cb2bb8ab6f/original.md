Plugin for letting `@ref` links fall back to `@extref` links.

!!! warning
    This plugin is available only with `Documenter >= v1.3.0` and should be considered as experimental.


```julia
fallbacks = ExternalFallbacks(pairs...)
```

defines a mapping of `@ref`-slugs to `@external` links. If an `@ref` cannot be resolved locally, the [`InterLinks`](@ref) plugin will be used to resolve it with the `@extref` link target defined in the mapping.

The `@ref`-slug can be found in the message printed by `Documenter` when it cannot resolve an `@ref` link, e.g.,

```
Error: Cannot resolve @ref for 'makedocs' …
Error: Cannot resolve @ref for 'Other-Output-Formats'
```

from some unresolvable links ```[`makedocs`](@ref)``` and `[Other Output Formats](@ref)`.

The "slug" is the string inside the quotes. It should be mapped to a complete `@extref` link, e.g.,

```julia
fallbacks = ExternalFallbacks(
    "makedocs" => "@extref Documenter.makedocs",
    "Other-Output-Formats" =>  "@extref Documenter `Other-Output-Formats`",
)
```

This will then resolve the link ```[`makedocs`](@ref)``` as if it had been written as ```[`makedocs`](@extref Documenter.makedocs)```, and `[Other Output Format](@ref)` as if it had been written as ```[Other Output Format](@extref Documenter `Other-Output-Formats`)``` and link to [`makedocs`](@ref) and [Other Output Formats](@ref), respectively.
