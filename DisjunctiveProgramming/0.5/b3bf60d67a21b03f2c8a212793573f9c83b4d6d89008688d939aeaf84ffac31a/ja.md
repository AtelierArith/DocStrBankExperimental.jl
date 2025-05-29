```
JuMP.fix(vref::LogicalVariableRef, value::Bool)::Nothing
```

論理変数を値に固定します。既存の固定制約がある場合はそれを更新し、そうでない場合は新しい制約を作成します。
