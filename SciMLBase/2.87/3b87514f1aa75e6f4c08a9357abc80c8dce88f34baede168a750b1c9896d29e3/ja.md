```
resize_non_user_cache!(integrator::DEIntegrator,k::Int)
```

非ユーザー向けのキャッシュをサイズ `k` のDEに互換性を持たせるようにサイズ変更します。これにはヤコビ行列キャッシュのサイズ変更が含まれます。

!!! note
    多くの場合、[`resize!`](@ref) は単に [`full_cache`](@ref) 変数のサイズを変更し、その後この関数を呼び出します。このより細かい制御は、一部の `AbstractArray` 操作に必要です。

