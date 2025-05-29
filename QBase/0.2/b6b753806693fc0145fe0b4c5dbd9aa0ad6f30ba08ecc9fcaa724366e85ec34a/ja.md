```
JointProbabilities(
    distribution :: Matrix{<:Real};
    atol=ATOL :: Float64
) <: JointProbabilityDistribution
```

離散確率分布を表す構造体です。周辺分布のすべての要素は正でなければならず、その合計は1でなければなりません。便利なことに、`JointProbabilities`は`ConditionalDistribution`と`ProbabilityDistribution`を渡すことによっても構築できます。

```
JointProbabilities(
    priors :: AbstractVector{<:Real},
    conditionals :: AbstractMatrix{<:Real};
    atol=ATOL :: Float64
)
```

または、2つの`ProbabilityDistribution`を提供することもできます。

```
JointProbabilities(
    priors1 :: AbstractVector{<:Real},
    priors2 :: AbstractVector{<:Real};
    atol=ATOL :: Float64
)
```

結合確率分布が無効な場合、`DomainError`がスローされます。
