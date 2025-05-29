```
throw_error(::ProbabilityLessThanZeroError)
```

確率がゼロ未満の場合にエラーをスローします。

# 例

```julia
throw_error(ProbabilityLessThanZeroError()) # "確率は0未満です（ヒント：確率ではなく、エラーをスローしました）"というメッセージでエラーをスローします
```
