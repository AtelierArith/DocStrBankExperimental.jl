```
hook_cache(stack::PluginStack, hookfns)
hook_cache(plugins, hookfns)
```

Create a cache of `HookList`s for a PluginStack or from lists of plugins and hook functions.

Returns a NamedTuple with an entry for every handler.

# Examples

```julia
cache = hook_cache([Plugin1(), Plugin2()], [hook1, hook2])
cache.hook1()
```
