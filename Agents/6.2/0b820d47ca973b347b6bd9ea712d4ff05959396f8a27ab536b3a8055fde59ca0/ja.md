```
GridSpaceSingle(d::NTuple{D, Int}; periodic = true, metric = :chebyshev)
```

これは、位置ごとに1つのエージェントのみを許可し、この知識を利用して[`GridSpace`](@ref)に対して大幅なパフォーマンス向上を提供する[`GridSpace`](@ref)の特化版です。

この空間は**内部使用のためにエージェントID = 0を予約します。** エージェントは、正または負の非ゼロIDで初期化する必要があります。これは内部でチェックされません。

すべての引数とキーワードは、[`GridSpace`](@ref)とまったく同じように動作します。
