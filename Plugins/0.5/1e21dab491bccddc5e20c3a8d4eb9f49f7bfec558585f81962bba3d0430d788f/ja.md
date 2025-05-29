```
hook_cache(stack::PluginStack, hookfns)
hook_cache(plugins, hookfns)
```

PluginStackのための`HookList`のキャッシュを作成するか、プラグインとフック関数のリストから作成します。

すべてのハンドラーのエントリを持つNamedTupleを返します。

# 例

```julia
cache = hook_cache([Plugin1(), Plugin2()], [hook1, hook2])
cache.hook1()
```
