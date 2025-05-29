```
UniformGenerativeInfo <: AbstractGenerativeInfo
```

均一に生成されるサポートのための `DataType` で、有限要素の間（すなわち、既存のサポートの間）で生成されます。これらの生成サポートは、名目ドメイン [0, 1] にある `support_basis` によって記述されます。コンストラクタは次の形式です：

```
    UniformGenerativeInfo(support_basis::Vector{<:Real}, label::DataType, 
                          [lb::Real = 0, ub::Real = 1])
```

ここで、`support_basis` は [`lb`, `ub`] の範囲で定義されています。

**フィールド**

  * `support_basis::Vector{Float64}`: 各有限要素のために変換される [0, 1] で定義された生成サポートの基盤。
  * `label::DataType`: 各生成サポートに与えられるユニークなラベル。
