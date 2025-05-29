```
concat(name::AbstractString, v::AbstractVertex, vs::AbstractVertex...; traitfun=identity, layerfun=identity)
```

名前 `name` を持つ頂点を返し、入力を活性化（例えば、畳み込みの場合はチャネル、密な場合は最初の次元）次元に沿って連結します。

名前は表示やログに使用されるだけで、一意である必要はありません（ただし、そうするのが良いアイデアである可能性があります）。

入力は互換性のある活性化形状を持っている必要があり、そうでない場合は例外がスローされます。

キーワード引数 `layerfun` は計算をラップするために使用でき、例えば [`ActivationContribution`](@ref) の中で使用できます。

キーワード引数 `traitfun` は、頂点の `MutationTrait` を `DecoratingTrait` の中でラップするために使用できます。

`NaiveNASlib.conc` も参照してください。
