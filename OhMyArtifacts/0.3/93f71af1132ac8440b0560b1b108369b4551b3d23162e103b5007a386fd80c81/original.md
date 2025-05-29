```
@my_artifact op name [hash]
```

Convenient macro for working with "Artifacts.toml". Requiring a global variable `my_artifacts` storing the path  to "Artifacts.toml" (created by `@my_artifacts_toml!`) to work correctly.

Usage:

1. `@my_artifact :bind name hash` => `bind_my_artifact!(my_artifacts, name, hash)`
2. `@my_artifact :hash name` => `my_artifact_hash(name, my_artifacts)`
3. `@my_artifact :unbind name` => `unbind_my_artifact!(my_artifacts, name)`
4. `@my_artifact :download name url downloadf kwarg...` =>  `download_my_artifact!(downloadf, url, name, my_artifacts; kwarg...)`

See also: [`bind_my_artifact!`](@ref), [`my_artifact_hash`](@ref),  [`unbind_my_artifact!`](@ref), [`@my_artifacts_toml`](@ref)
