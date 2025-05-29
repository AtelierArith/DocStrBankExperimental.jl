```
delete_preferences!(uuid_or_module_or_name, prefs::String...;
                    block_inheritance::Bool = false, export_prefs=false, force=false)
```

Deletes a series of preferences for the given uuid::UUID/module::Module/name::String, identified by the keys passed in as `prefs`.

See the docstring for [`set_preferences!`](@ref) for more details.
