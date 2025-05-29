```
FunctionalVPolicy(evaluator, domain, spec)
```

状態値が `evaluator` によって定義されるポリシーソリューションであり、`evaluator` は各 `state` に対する値の推定を出力する一引数関数です。ポリシーが各状態に対するアクションQ値を導出する方法を知るために、ドメインと仕様も提供する必要があります。
