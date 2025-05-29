```
	eval_febe!(result, FEBE::FEBasisEvaluator, j::Int, i::Int, offset::Int = 0, factor = 1)
```

FEBasisEvaluatorのj番目の基底関数をi番目の数値積分点で評価し、結果をresultに書き込みます（オフセットから始まり、指定された係数で）。
