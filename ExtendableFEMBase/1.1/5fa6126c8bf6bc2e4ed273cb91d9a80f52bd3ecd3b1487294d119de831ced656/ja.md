```julia
abstract type Reconstruct{FETypeR, O} <: ??
```

再構成演算子: 再構成された有限要素関数のバージョンを評価します。

FETypeRは再構成空間を指定します（適用される有限要素のために定義する必要があります）。Oは評価されるStandardFunctionOperatorを指定します。
