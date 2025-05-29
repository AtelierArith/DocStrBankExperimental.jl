```
SimpleInitiator(threshold = 1.0) <: InitiatorRule
```

[`PDVec`](@ref) または [`InitiatorDVec`](@ref) に渡されるイニシエータールール。イニシエータは、係数の大きさ `abs(v[add]) > threshold` を持つ構成 `add` です。`threshold` はキーワード引数として渡すことができます。ルール：

  * イニシエータはどこでもスポーンできます。
  * 非イニシエータはスポーンできません。

[`InitiatorRule`](@ref) を参照してください。
