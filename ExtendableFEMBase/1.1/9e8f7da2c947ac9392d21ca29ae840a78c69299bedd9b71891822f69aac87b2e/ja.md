```
function evaluate!(
	result,
	PE::PointEvaluator,
	x
	)
```

指定された座標 x で PointEvaluator を評価します。（これを行うために、内部的に CellFinder を呼び出してセルと x のバリセントリック座標を見つけ、evaluate_bary! を呼び出します。）
