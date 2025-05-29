```
compute_Mlincomb_from_MM(nep::NEP,λ::Number,V,a)
```

この関数は、`compute_MM`への呼び出しを行うことによって`compute_Mlincomb`関数呼び出しを提供します。基礎となる数学的関係は、githubのイシュー#2および#3で説明されています。

標準的な使用法は、次のコマンドによって行われます：

```julia
compute_Mlincomb(nep::MyNEP,λ::Number,V,a)=compute_Mlincomb_from_MM(nep,λ,V,a)
```
