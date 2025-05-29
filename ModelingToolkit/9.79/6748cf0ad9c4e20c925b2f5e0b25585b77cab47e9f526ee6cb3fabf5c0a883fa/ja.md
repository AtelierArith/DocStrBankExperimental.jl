```
tunable_parameters(sys, p = parameters(sys; initial_parameters = true); default=true)
```

`sys`のすべての`tunable`としてマークされたパラメータを取得します。

キーワード引数`default`は、`tunable`メタデータがない変数をチューニング可能と見なすかどうかを示します。

チューニング可能なパラメータを作成するには、

```
@parameters u [tunable=true]
```

`split = true`（デフォルト）で作成されたシステムと、この関数に`default = true`が渡された場合、返されるパラメータの順序は、`MTKParameters`のチューニング可能部分に格納されている順序です。配列変数はスカラー化されないことに注意してください。チューニング可能部分のフラットな表現を取得するには、`Symbolics.scalarize(tunable_parameters(sys))`を呼び出し、結果の配列を連結します。

他にも[`getbounds`](@ref)、[`istunable`](@ref)、[`MTKParameters`](@ref)、[`complete`](@ref)を参照してください。
