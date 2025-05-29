```
tunable_parameters(sys, p = parameters(sys); default=false)
```

`sys` のすべてのパラメータを取得します。これらは `tunable` としてマークされています。

キーワード引数 `default` は、`tunable` メタデータがない変数をチューニング可能と見なすかどうかを示します。

チューニング可能なパラメータを作成するには

```
@parameters u [tunable=true]
```

も参照してください [`getbounds`](@ref), [`istunable`](@ref)
