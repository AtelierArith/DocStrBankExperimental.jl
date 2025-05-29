```
execute_function_safely(Func::Function, x::Array{T,1}; type_check::Bool = false, quiet_errors::Bool = true) where T<:Real
```

この関数は、固定点を求めるために実行される関数を作成します。これはエクスポートされていないヘルパー関数です。

### 入力

  * `Func` - fixed_pointへの関数入力
  * `x` - 関数を評価する点。
  * `type_check` - 関数の型の安定性をチェックし、整数の入力ベクトルが浮動小数点数のベクトルに変わる場合にエラーを報告するべきかどうか。

### 戻り値

  * `FunctionEvaluationResult`

### 例

```
Func(x) = sqrt(x)
execute_function_safely(Func, [-1.0,0.0,1.0])
execute_function_safely(Func,[Missing(),0.0,1.0])
execute_function_safely(Func,[7.0,0.0,1.0])
execute_function_safely(Func,[NaN,0.0,1.0])
execute_function_safely(Func,[Inf,0.0,1.0])
execute_function_safely(Func,-1.0)
execute_function_safely(Func,Missing())
execute_function_safely(Func,1.0)
execute_function_safely(Func,NaN)
execute_function_safely(Func,Inf)
```
