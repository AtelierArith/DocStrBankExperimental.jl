```
RangeMatrix(rs::AbstractVector{T}) where T <: AbstractRange
```

RangeMatrixは、範囲のベクトルの単純な行列表現であり、各範囲が1つの列を表します。範囲のベクトルを使用してRangeMatrixを構築します。範囲はすべて同じ長さでなければなりません。

すべての範囲が同じタイプであり、具体的に型付けされたベクトルにある場合にのみ効率的であることに注意してください。
