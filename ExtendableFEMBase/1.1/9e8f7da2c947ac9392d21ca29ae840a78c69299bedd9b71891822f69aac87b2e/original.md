```
function evaluate!(
	result,
	PE::PointEvaluator,
	x
	)
```

Evaluates the PointEvaluator at the specified coordinates x. (To do so it internally calls CellFinder to find the cell and the barycentric coordinates of x and calls evaluate_bary!.)
