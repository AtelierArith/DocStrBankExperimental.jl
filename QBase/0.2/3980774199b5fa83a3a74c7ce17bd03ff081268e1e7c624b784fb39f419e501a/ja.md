```
outcome_probabilities(
    conditionals::ConditionalDistribution,
    priors :: ProbabilityDistribution;
    atol=ATOL :: Float64
) :: ProbabilityDistribution
```

条件付き確率と事前確率に基づいて各結果の確率を返します。便利のため、このメソッドは抽象ベクトル/行列で呼び出すこともできます。

```
outcome_probabilities(
    conditionals :: AbstractMatrix{<:Real},
    priors :: AbstractVector{<:Real};
    atol=ATOL :: Float64
)
```

さらに、引数の順序を逆にすることもできます。構築されたベクトルが有効な確率分布でない場合、`DomainError`がスローされます。
