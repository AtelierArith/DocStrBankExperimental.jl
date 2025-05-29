```
sysm, T, HF = hess_form(sys)
```

`sys`をヘッセンベルグ形式に変換します。

ヘッセンベルグ形式は、`A`が上部ヘッセンベルグ構造を持つことによって特徴付けられます。`T`は、次のようにシステムに適用される類似変換です。

```julia
sysm ≈ similarity_transform(sys, T)
```

`HF`は`A`のヘッセンベルグ因子分解です。

[`modal_form`](@ref)および[`schur_form`](@ref)も参照してください。
