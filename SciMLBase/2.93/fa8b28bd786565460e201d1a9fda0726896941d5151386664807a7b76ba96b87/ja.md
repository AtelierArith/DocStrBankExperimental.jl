```
addat_non_user_cache!(i::DEIntegrator,idxs)
```

[`addat!`](@ref)は、インデックス`idxs`で非ユーザー向けキャッシュを追加します。これには、ヤコビアンキャッシュのサイズ変更が含まれます。

!!! note
    多くの場合、`addat!`は単に[`full_cache`](@ref)変数を`addat!`し、その後この関数を呼び出します。このより細かい制御は、一部の`AbstractArray`操作に必要です。

