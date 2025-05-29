```
PluginStack(plugins, hookfns = [])
```

Manages the plugins loaded into an application.

It provides fast access to the plugins by symbol, e.g. `pluginstack[:logger]`. Collection methods and iteration interface are implemented.

The pluginstack is created from a list of plugins, and optionally a list of hook functions. If hook functions are provided, the `hooks()`` function can be called to
