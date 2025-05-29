```
CoherentInitiator(threshold = 1.0) <: InitiatorRule
```

[`PDVec`](@ref) または [`InitiatorDVec`](@ref) に渡されるイニシエータールール。イニシエータは、係数が `abs(v[add]) > threshold` の構成 `add` です。`threshold` はキーワード引数として渡すことができます。ルール：

  * イニシエータはどこにでもスポーンできます。
  * 非イニシエータはイニシエータにスポーンできます。
  * 複数の非イニシエータは、イニシエータの閾値を超える値に貢献する場合、単一の非イニシエータにスポーンできます。

[`InitiatorRule`](@ref) を参照してください。
