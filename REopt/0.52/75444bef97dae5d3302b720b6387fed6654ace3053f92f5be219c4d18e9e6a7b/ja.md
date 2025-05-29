```
run_mpc(m::JuMP.AbstractModel, ps::AbstractVector{MPCInputs})
```

複数の `MPCInputs` を使用してモデル予測制御問題を解決します。

`MPCScenario` のキーに一致する結果の Dict を返します。
