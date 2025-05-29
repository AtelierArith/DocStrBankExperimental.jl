```
throw_error(::ExceededNumKrausOperators)
```

許可されたよりも多くのクラウス演算子が提示されたときにエラーをスローします。

# 例

```julia
throw_error(ExceededNumKrausOperators()) # "許可されたよりも多くのクラウス演算子が提示されました。再度確認してください。"というメッセージでエラーをスローします。
```
