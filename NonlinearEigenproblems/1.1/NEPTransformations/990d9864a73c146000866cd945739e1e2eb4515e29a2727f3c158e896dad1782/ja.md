```
mobius_transform(orgnep::NEP,[,a=1][,b=0][,c=0][,d=1])
```

nep (orgnep) $M(λ)v$ を新しい nep $T(λ)=M((aλ+b)/(cλ+d))$ に変換します。この関数は、`T` と `M` が同じ NEPタイプであることを保つように試みます（`shift_and_scale()` を参照）。タイプを保つことができない場合は、`MobiusTransformedNEP` を返します。一般的に、タイプを保つことを試みることが推奨されており、`MobiusTransformedNEP` の使用は NEPアクセスをかなり遅くする可能性があります。

# 例

```julia-repl
julia> nep0=nep_gallery("pep0")
julia> a=1; b=3; c=4; d=5;
julia> nep1=mobius_transform(nep0,a=a,b=b,c=c,d=d);
julia> s=3;
julia> opnorm(compute_Mder(nep0,(a*s+b)/(c*s+d))-compute_Mder(nep1,s))
0.0
```
