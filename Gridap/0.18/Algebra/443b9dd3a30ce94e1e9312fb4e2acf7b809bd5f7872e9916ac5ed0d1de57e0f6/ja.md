```
struct NLSolver <: NonlinearSolver
  # private fields
end
```

このソルバーを使用して生成されたキャッシュには、基盤となる `nlsolve` 関数によって生成された結果オブジェクトをホストする `result` フィールドがあります。これは、最新の解に対応しています。
