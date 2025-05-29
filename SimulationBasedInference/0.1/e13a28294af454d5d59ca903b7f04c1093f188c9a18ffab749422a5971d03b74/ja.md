```
SimulatorLikelihood(::Type{distType}, obs, data, prior, name=nameof(obs)) where {distType}
```

指定された分布タイプ、観測可能なデータソース、および事前分布を使用して `SimulatorLikelihood` を作成します。カスタム識別子は `name` 引数を介して指定することもでき、デフォルトでは観測可能なデータの名前が使用されます。
