```
shutdown!(plugin, args...)
```

Shut down the plugin.

This lifecycle hook will be called when the application unloads a plugin, e.g. before the application exits. Plugins.jl does not (yet) helps with this, application developers should do it manually.
