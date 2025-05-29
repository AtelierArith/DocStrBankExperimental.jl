```
@dataplugin plugin_variable
@dataplugin plugin_variable :default
```

変数 `plugin_variable` によって与えられたプラグインを、そのドキュメント（`@doc` によって取得）と共に登録します。第二引数として `:default` が与えられた場合、プラグインはデフォルトプラグインのリストにも追加されます。

これは、以下のパターンに対する小さな、しかし感謝される便利さとして機能します：

```julia
push!(PLUGINS, myplugin)
PLUGINS_DOCUMENTATION[myplugin.name] = @doc myplugin
push!(DEFAULT_PLUGINS, myplugin.name) # デフォルトにも追加する場合
```
