```
throw_error(::ProbabilityExceedsFifteenSixteensError)
```

15/16を超える確率が遭遇したときにエラーをスローします。通常、ノイズモデルの制限に関連しています。

# 例

```julia
throw_error(ProbabilityExceedsFifteenSixteensError()) # "Probability is greater than 15/16 (hint: error thrown in relation to noise model limitations)"というメッセージでエラーをスローします
```
