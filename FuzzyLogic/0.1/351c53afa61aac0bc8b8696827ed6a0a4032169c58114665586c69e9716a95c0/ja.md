```julia
struct LinearSugenoOutput{T} <: FuzzyLogic.AbstractSugenoOutputFunction
```

入力に対して一次多項式の関係を持つ出力変数を表します。Sugeno推論システムで使用されます。

  * `coeffs::Dictionaries.Dictionary{Symbol}`: 各入力変数に関連付けられた係数。
  * `offset::Any`: 出力のオフセット。
