```
model_psd_variables_as_free_variables!(problem::Problem, as_free)
```

`as_free`にある名前の正半定値変数を自由変数としてモデル化し、それらを補助的な正半定値変数と等しくするための追加の制約を加えます。
