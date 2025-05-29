```
throw_error(::ProbabilityExceedsOneError)
```

1より大きい確率が遭遇したときにエラーをスローします。

# 例

```julia
throw_error(ProbabilityExceedsOneError()) # "確率は1より大きい（ヒント：確率ではなくエラーをスローしました）"というメッセージでエラーをスローします
```
