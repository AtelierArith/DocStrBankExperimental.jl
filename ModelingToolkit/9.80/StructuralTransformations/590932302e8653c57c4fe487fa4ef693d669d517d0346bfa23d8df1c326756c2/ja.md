```
dae_index_lowering(sys::ODESystem; kwargs...) -> ODESystem
```

パンテリデスアルゴリズムを実行して、高次インデックスDAEをインデックス1 DAEに変換します。`kwargs`は[`pantelides!`](@ref)に転送されます。エンドユーザーは、内部でこの関数を呼び出す[`structural_simplify`](@ref)を代わりに呼び出すことを推奨します。
