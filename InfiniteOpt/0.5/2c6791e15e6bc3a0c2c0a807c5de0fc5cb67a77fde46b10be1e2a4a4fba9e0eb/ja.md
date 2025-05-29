```
expand_measure(expr, data::AbstractMeasureData,
               write_model::JuMP.AbstractModel)::JuMP.AbstractJuMPScalar
```

変数/パラメータ式 `expr` と測定データ `data` を含む測定の有限再定式化を返します。ここで `write_model` は、この拡張された式が使用されるターゲットモデルです。したがって、作成する必要のある変数はすべて `write_model` に追加されます。これらの変数を作成するために、適切に [`make_point_variable_ref`](@ref) および [`make_semi_infinite_variable_ref`](@ref) メソッドを使用する必要があります。この関数は内部関数として意図されていますが、サポートされていない `expr` タイプやユーザー定義の測定データタイプに対して拡張する必要があります。主に、これはユーザーメソッド [`expand`](@ref) および [`expand_all_measures!`](@ref) を有効にするために利用されます。
