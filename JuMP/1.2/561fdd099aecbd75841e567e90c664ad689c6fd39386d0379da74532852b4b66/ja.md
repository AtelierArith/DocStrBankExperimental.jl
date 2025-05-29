```
optimizer_index(v::VariableRef)::MOI.VariableIndex
```

`v`に対応する変数のインデックスを最適化モデルから返します。最適化プログラムが設定されていない場合は[`NoOptimizer`](@ref)をスローし、最適化プログラムが設定されているが接続されていない場合は`ErrorException`をスローします。
