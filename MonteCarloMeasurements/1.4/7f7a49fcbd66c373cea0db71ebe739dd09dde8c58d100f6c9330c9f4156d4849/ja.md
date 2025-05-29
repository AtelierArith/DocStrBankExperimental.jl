```
@bypmap f(p, args...)
```

並列 `pmap` を使用して粒子または粒子のベクトルで `f` を呼び出します。これは、[`register_primitive`](@ref) を使用して `f` を登録するのが失敗した場合に利用できます。`bymap` が失敗した場合は、[`Workspace`](@ref) も参照してください。
