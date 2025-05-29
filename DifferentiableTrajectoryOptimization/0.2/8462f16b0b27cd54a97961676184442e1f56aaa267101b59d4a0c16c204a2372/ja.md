```
Optimizer(problem, solver)
```

指定された`sovler`バックエンドを使用して、与えられた`problem`のための`Optimizer`を構築します。

サポートされているバックエンドは次のとおりです：

  * [`QPSolver`](@ref)
  * [`NLPSolver`](@ref)
  * [`MCPSolver`](@ref)

詳細については、彼らのドキュメントを参照してください。

# 例

```@example running_example
solver = QPSolver()
optimizer = Optimizer(problem, solver)
```
