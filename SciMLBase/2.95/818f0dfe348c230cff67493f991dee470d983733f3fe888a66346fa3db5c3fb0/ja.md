```
deleteat_non_user_cache!(integrator::DEIntegrator,idxs)
```

[`deleteat!`](@ref)は、インデックス`idxs`で非ユーザー向けキャッシュを削除します。これには、ヤコビ行列キャッシュのサイズ変更が含まれます。

!!! note
    多くの場合、`deleteat!`は単に[`full_cache`](@ref)変数を`deleteat!`し、その後この関数を呼び出します。このより細かい制御は、一部の`AbstractArray`操作に必要です。

