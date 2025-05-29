```
concat(v::AbstractVertex, vs::AbstractVertex...; traitfun=identity, layerfun=identity)
```

入力を活性化（例えば、畳み込みの場合はチャネル、密な場合は最初の次元）次元に沿って連結する頂点を返します。

入力は互換性のある活性化形状を持っている必要があり、そうでない場合は例外がスローされます。

キーワード引数 `layerfun` は計算をラップするために使用できます。例えば、[`ActivationContribution`](@ref) の中で。

キーワード引数 `traitfun` は、頂点の `MutationTrait` を `DecoratingTrait` にラップするために使用できます。

`NaiveNASlib.conc` も参照してください。
