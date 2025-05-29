```
throw_error(::ProbabilityExceedsOneHalfError)
```

1/2 より大きい確率が遭遇したときにエラーをスローします。通常、ノイズモデルの制限に関連しています。

# 例

```julia
throw_error(ProbabilityExceedsOneHalfError()) # "Probability is greater than 1/2 (hint: error thrown in relation to noise model limitations)" というメッセージでエラーをスローします
```
