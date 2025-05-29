```
constraint_ref_with_index(model::AbstractModel, index::MOI.ConstraintIndex)
```

`index`に対応する`model`の`ConstraintRef`を返します。

この関数は、JuMPおよびいくつかのJuMP拡張によって内部で使用されるヘルパー関数です。ユーザーコードで呼び出す必要はありません。
