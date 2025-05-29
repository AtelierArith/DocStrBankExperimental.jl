```
Probabilities( distribution :: Vector{<:Real}; atol=ATOL :: Float64 ) <: ProbabilityDistribution
```

離散確率分布を表す構造体です。周辺分布のすべての要素は正でなければならず、その合計は1でなければなりません。
