```
setup!(plugin, deps, args...)
```

Initialize the plugin with the given dependencies and arguments (e.g. shared state).

This lifecycle hook will be called when the application loads a plugin. Plugins.jl does not (yet) helps with this, application developers should do it manually, right after the PluginStack was created, before the hook_cache() call.
