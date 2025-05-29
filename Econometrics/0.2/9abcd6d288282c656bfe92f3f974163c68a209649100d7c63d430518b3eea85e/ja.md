```
coeftable(obj::EconometricModel;
	  level::Real = 0.95)
coeftable(obj::EconometricModel{<:LinearModelEstimators};
	  level::Real = 0.95,
	  vce::VCE = obj.vce)
```

クラス `CoefTable` のテーブルを返し、係数と関連する統計を含みます。`level` は信頼区間のレベルを決定します（デフォルトは95%）。`vce` は分散共分散推定量を決定します（デフォルトは `OIM`）。
