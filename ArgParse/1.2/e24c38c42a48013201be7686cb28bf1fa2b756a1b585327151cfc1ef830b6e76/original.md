```
import_settings!(settings, other_settings [,args_only])
```

Imports `other_settings` into `settings`, where both are [`ArgParseSettings`](@ref) objects. If `args_only` is `true` (this is the default), only the argument table will be imported; otherwise, the default argument group will also be imported, and all general settings except `prog`, `description`, `epilog`, `usage` and `version`.

Sub-settings associated with commands will also be imported recursively; the `args_only` setting applies to those as well. If there are common commands, their sub-settings will be merged.

While importing, conflicts may arise: if `settings.error_on_conflict` is `true`, this will result in an error, otherwise conflicts will be resolved in favor of `other_settings` (see the [Conflicts and overrides](@ref) section for a detailed discussion of how conflicts are handled).

Argument groups will also be imported; if two groups in `settings` and `other_settings` match, they are merged (groups match either by name, or, if unnamed, by their description).

Note that the import will have effect immediately: any subsequent modification of `other_settings` will not have any effect on `settings`.

This function can be used at any time.
