```
NodeData
```

`NLPExpr`[@ref]で使用される式木に値を格納するための`DataType`です。許可される値の型には以下が含まれます：

  * `Real`: 定数
  * `GeneralVariableRef`: 最適化変数
  * `JuMP.GenericAffExpr{Float64, GeneralVariableRef}`: アフィン式
  * `JuMP.GenericQuadExpr{Float64, GeneralVariableRef}`: 二次式
  * `Symbol`: 登録されたNLP関数名。

**フィールド**

  * `value`: 格納された値。
