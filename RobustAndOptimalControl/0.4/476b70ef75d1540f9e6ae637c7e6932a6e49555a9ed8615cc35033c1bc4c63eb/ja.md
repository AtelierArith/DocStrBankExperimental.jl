```
sysm, T, SF = schur_form(sys)
```

`sys`をシュール形式に変換します。

シュール形式は、`A`がシュールであり、`A`の固有値の実数値が主対角線上にあることによって特徴付けられます。`T`は、次のようにシステムに適用される類似変換です。

```julia
sysm ≈ similarity_transform(sys, T)
```

`SF`は`A`のシュール因子分解です。

[`modal_form`](@ref)および[`hess_form`](@ref)も参照してください。
