```
abstract type Interpreter end
```

この型をサブタイプとするインタプリタは、基本型に対して定義されているJuliaInterpreterの特定のメソッドをオーバーロードすることによって、自身の評価戦略を実装できます。`Interpreter`のデフォルトの動作は[`RecursiveInterpreter`](@ref)と同じであり、すべての`:call`式を再帰的に解釈します。
