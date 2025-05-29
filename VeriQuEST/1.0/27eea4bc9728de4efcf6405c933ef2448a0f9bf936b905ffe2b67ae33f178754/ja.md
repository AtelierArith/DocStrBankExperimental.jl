```
throw_error(::ProbabilityExceedsNoErrorExceeded)
```

確率が1からのエラーなしを超えるとエラーをスローします。

# 例

```julia
throw_error(ProbabilityExceedsNoErrorExceeded()) # "確率が1からのエラーなしを超えています。"というメッセージでエラーをスローします。
```
