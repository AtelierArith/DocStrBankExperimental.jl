```
collapse(x::TS, at::Function; fun::Function=last, args...)::TS
```

関数 `fun` を `at` によって定義された期間の境界（例：`eom`、`boq` など）で計算し、結果の時系列を返します。

キーワード引数 (`args...`) は関数 `fun` に渡されます。
