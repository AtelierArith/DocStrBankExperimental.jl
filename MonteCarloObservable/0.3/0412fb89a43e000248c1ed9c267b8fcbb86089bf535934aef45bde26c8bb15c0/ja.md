```
saveobs(obs::Observable{T}[, filename::AbstractString, entryname::AbstractString])
```

オブザーバブルの完全な表現をJLDファイルに保存します。

デフォルトのファイル名は "Observables.jld" で、デフォルトのエントリ名は `name(obs)` です。

関連情報は [`loadobs`](@ref) を参照してください。
