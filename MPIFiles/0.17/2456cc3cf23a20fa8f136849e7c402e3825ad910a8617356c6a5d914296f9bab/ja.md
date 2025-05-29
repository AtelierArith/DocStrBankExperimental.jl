```julia
mutable struct TransferFunction
```

  * `freq::Vector{Float64}`
  * `data::Matrix{ComplexF64}`
  * `interpolator::Vector{Interpolations.AbstractInterpolation}`
  * `inductionFactor::Vector{Float64}`
  * `units::Vector{Unitful.FreeUnits}`

```
TransferFunction(freq::Vector, data::Array, [phasedata]; [inductionFactor], [units])
```

データ配列 `data` を周波数 `freq` で使用して `TransferFunction` を作成します。`freq` は Hz で指定されるか、Unitful 周波数単位が付与されている必要があります。`data` は [周波数, チャンネル] の形状を持つ必要があります。`data` は複素数または実数のいずれかであり、`data` が実数の場合、ラジアンでの位相を表す第二の配列 `phasedata` を渡すことができます。振幅と位相の両方に Unitful 単位を持たせることができます。

# オプションのキーワード引数:

  * `inductionFactor::Vector{<:Real}`: 各チャンネルの誘導因子
  * `units::Vector`: 各チャンネルの単位で、Unitful.FreeUnits または Unitful 単位として解析可能な文字列のいずれかである必要があります。このキーワードを使用する代わりに、`data` に Unitful 単位が付与されている場合、units キーワード引数は無視されます。
