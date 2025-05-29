```
hooks(app)
hooks(pluginstack::PluginStack)
```

Create or get a hook cache for `stack`.

The first form can be used when `pluginstack` is stored in `app.plugins` (the recommended pattern).

When this function is called first time on a `PluginStack`, the hooks cache will be created by calling `hook_cache()`, and stored in `pluginstack` for quick access later.
