```
reformulate_model(model::JuMP.AbstractModel, method::AbstractSolutionMethod = BigM())
```

指定された`method`を使用して`GDPModel`を再定式化します。再定式化の前に、すべての以前の再定式化変数と制約が削除されます。
