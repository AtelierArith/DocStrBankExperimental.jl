```
fluxvertex(name::AbstractString, l, in::AbstractVertex; layerfun=LazyMutable, traitfun=validated())
```

名前 `name` を持ち、レイヤー `l` をラップし、入力頂点 `in` を持つ頂点を返します。

名前は表示やログに使用されるだけで、一意である必要はありません（ただし、そうするのが良いアイデアである可能性があります）。

キーワード引数 `layerfun` は計算をラップするために使用できます。例えば、[`ActivationContribution`](@ref) の中で。

キーワード引数 `traitfun` は、頂点の `MutationTrait` を `DecoratingTrait` の中でラップするために使用できます。
