```
hooks(app)
hooks(pluginstack::PluginStack)
```

`stack`のためのフックキャッシュを作成または取得します。

最初の形式は、`pluginstack`が`app.plugins`に格納されている場合（推奨パターン）に使用できます。

この関数が`PluginStack`で初めて呼び出されると、フックキャッシュは`hook_cache()`を呼び出すことによって作成され、後で迅速にアクセスできるように`pluginstack`に格納されます。
