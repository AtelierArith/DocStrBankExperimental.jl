```
IntegralProblem(f, domain, [p=NullParameters]; kwargs...)
```

## 引数

  * `f::AbstractIntegralFunction`: 積分する関数
  * `domain`: 積分する範囲、例えば `(lb, ub)`
  * `p`: 被積分関数に渡すパラメータ

## キーワード

追加のキーワードはソルバーに直接渡されます。
