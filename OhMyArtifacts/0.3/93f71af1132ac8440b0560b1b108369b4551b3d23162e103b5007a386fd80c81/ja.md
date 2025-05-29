```
@my_artifact op name [hash]
```

「Artifacts.toml」を操作するための便利なマクロです。正しく動作するためには、`@my_artifacts_toml!`によって作成された「Artifacts.toml」へのパスを格納するグローバル変数`my_artifacts`が必要です。

使用法：

1. `@my_artifact :bind name hash` => `bind_my_artifact!(my_artifacts, name, hash)`
2. `@my_artifact :hash name` => `my_artifact_hash(name, my_artifacts)`
3. `@my_artifact :unbind name` => `unbind_my_artifact!(my_artifacts, name)`
4. `@my_artifact :download name url downloadf kwarg...` =>  `download_my_artifact!(downloadf, url, name, my_artifacts; kwarg...)`

関連情報: [`bind_my_artifact!`](@ref), [`my_artifact_hash`](@ref),  [`unbind_my_artifact!`](@ref), [`@my_artifacts_toml`](@ref)
