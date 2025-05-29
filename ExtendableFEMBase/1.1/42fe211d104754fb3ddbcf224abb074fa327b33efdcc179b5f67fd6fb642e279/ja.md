```
	eval_febe!(result, FEBE::FEBasisEvaluator, j::Int, i::Int, offset::Int = 0, factor = 1)
```

与えられた係数を持つ基底関数の線形結合を i 番目の数値積分点で評価し、結果を result に書き込みます（オフセットから始まり、指定された係数で）。
