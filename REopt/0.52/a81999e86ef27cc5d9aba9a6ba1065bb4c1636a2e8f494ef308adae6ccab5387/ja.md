```
run_mpc(m::JuMP.AbstractModel, fp::String)
```

JSONファイルに保存されたファイルパス`fp`で定義された`MPCScenario`を使用してモデル予測制御問題を解決します。

`MPCScenario`のキーに一致する結果のDictを返します。
