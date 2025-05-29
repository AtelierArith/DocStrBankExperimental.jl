```
function eval_div(UD::AbstractUserDataType) -> Function
```

UDのDataFunctionの発散をx（およびUDが時間に依存する場合はt）で評価して返す関数を提供します。導関数はForwardDiffによって計算されます。
