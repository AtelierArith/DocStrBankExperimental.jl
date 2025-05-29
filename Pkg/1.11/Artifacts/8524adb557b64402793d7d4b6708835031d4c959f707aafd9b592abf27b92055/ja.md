```
unbind_artifact!(artifacts_toml::String, name::String; platform = nothing)
```

指定された`name`を`(Julia)Artifacts.toml`ファイルから解除します。ファイル内にそのようなバインディングが存在しない場合は、静かに失敗します。
