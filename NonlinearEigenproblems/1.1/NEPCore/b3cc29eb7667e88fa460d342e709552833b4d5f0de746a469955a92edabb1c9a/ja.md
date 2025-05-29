```
compute_Mlincomb_from_Mder(nep::NEP,λ::Number,V,a)
```

この関数は `compute_Mder` を呼び出すことで `Mlincomb` を計算します。この関数は行列の構築を必要とするため遅くなります。通常はこのようにオーバーロードして使用します。

```julia
    compute_Mlincomb(nep::MyNEP,λ::Number,V,a)=compute_Mlincomb_from_Mder(nep,λ,V,a)
```
