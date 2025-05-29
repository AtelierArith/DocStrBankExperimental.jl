```
fluxvertex(l, in::AbstractVertex; layerfun=LazyMutable, traitfun=validated())
```

レイヤー `l` をラップし、入力ベクトル `in` を持つベクトルを返します。

キーワード引数 `layerfun` は、計算をラップするために使用できます。例えば、[`ActivationContribution`](@ref) の中で。

キーワード引数 `traitfun` は、ベクトルの `MutationTrait` を `DecoratingTrait` の中でラップするために使用できます。
