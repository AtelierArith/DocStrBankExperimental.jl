```
(D,V)=get_deflated_eigpairs(S,V,n)
(D,V)=get_deflated_eigpairs(dnep::DeflatedNEP [λ,v])
```

不変ペア `S,V` の固有値 `D` のベクトルと対応する固有ベクトル `V` の行列を返します。固有対は、`DeflatedNEP` の背後にある元の問題に対応しています。オプションのパラメータ `λ,v` は、追加の固有対を含めることを可能にします。基本的に、オプションのパラメータは、脱落を拡張し、キーワード引数で `get_deflated_eigpairs` を実行することを意味します。すなわち、

```julia
(D,V)=get_deflated_eigpairs(deflate_eigpair(dnep,λ,v))`
```

[`deflate_eigpair`](@ref) の例を参照してください。
