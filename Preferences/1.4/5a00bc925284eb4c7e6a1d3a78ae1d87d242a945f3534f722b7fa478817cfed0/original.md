```
set_preferences!(uuid_or_module_or_name, prefs::Pair{String,Any}...;
                 export_prefs=false, active_project_only=true, force=false)
```

Sets a series of preferences for the given uuid::UUID/module::Module/name::String, identified by the pairs passed in as `prefs`.  Preferences are loaded from `Project.toml` and `LocalPreferences.toml` files on the load path, merging values together into a cohesive view, with preferences taking precedence in `LOAD_PATH` order, just as package resolution does.  Preferences stored in `Project.toml` files are considered "exported", as they are easily shared across package installs, whereas the `LocalPreferences.toml` file is meant to represent local preferences that are not typically shared.  `LocalPreferences.toml` settings override `Project.toml` settings where appropriate.

After running `set_preferences!(uuid, "key" => value)`, a future invocation of `load_preference(uuid, "key")` will generally result in `value`, with the exception of the merging performed by `load_preference()` due to inheritance of preferences from elements higher up in the `load_path()`.  To control this inheritance, there are two special values that can be passed to `set_preferences!()`: `nothing` and `missing`.

  * Passing `missing` as the value causes all mappings of the associated key to be removed from the current level of `LocalPreferences.toml` settings, allowing preferences set higher in the chain of preferences to pass through.  Use this value when you want to clear your settings but still inherit any higher settings for this key.
  * Passing `nothing` as the value causes all mappings of the associated key to be removed from the current level of `LocalPreferences.toml` settings and blocks preferences set higher in the chain of preferences from passing through.  Internally, this adds the preference key to a `__clear__` list in the `LocalPreferences.toml` file, that will prevent any preferences from leaking through from higher environments.

Note that the behaviors of `missing` and `nothing` are both similar (they both clear the current settings) and diametrically opposed (one allows inheritance of preferences, the other does not).  They can also be composed with a normal `set_preferences!()` call:

```julia
@set_preferences!("compiler_options" => nothing)
@set_preferences!("compiler_options" => Dict("CXXFLAGS" => "-g", LDFLAGS => "-ljulia"))
```

The above snippet first clears the `"compiler_options"` key of any inheriting influence, then sets a preference option, which guarantees that future loading of that preference will be exactly what was saved here.  If we wanted to re-enable inheritance from higher up in the chain, we could do the same but passing `missing` first.

The `export_prefs` option determines whether the preferences being set should be stored within `LocalPreferences.toml` or `Project.toml`.

The `active_project_only` flag ensures that the preference is set within the currently active project (as determined by `Base.active_project()`), and if the target package is not listed as a dependency, it is added under the `extras` section.  Without this flag set, if the target package is not found in the active project, `set_preferences!()` will search up the load path for an environment that does contain that module, setting the preference in the first one it finds.  If none are found, it falls back to setting the preference in the active project and adding it as an extra dependency.
