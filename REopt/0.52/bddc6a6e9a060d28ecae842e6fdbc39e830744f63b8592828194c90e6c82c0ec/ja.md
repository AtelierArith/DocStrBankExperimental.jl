```
run_mpc(m::JuMP.AbstractModel,  d::Dict)
```

辞書 `d` で定義された `MPCScenario` を使用してモデル予測制御問題を解決します。

`MPCScenario` のキーに一致する結果の辞書を返します。
