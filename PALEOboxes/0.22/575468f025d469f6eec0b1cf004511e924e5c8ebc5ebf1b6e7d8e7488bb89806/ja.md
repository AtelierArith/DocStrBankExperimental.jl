```
allocate_variables!(
    vars, modeldata, arrays_idx; 
    [, eltypemap::Dict{String, DataType}],
    [, default_host_dependent_field_data=nothing],
    [, allow_base_link=true],
    [. use_base_transfer_jacobian=true],
    [, use_base_vars=String[]],
    [, check_units_opt=:no])
```

[`VariableDomain`](@ref)s `vars` のために `modeldata` 配列セット `arrays_idx` にメモリを割り当てるかリンクします。

割り当てられた配列の要素型は `eltype(modeldata, arrays_idx)` によって決定されます（通常のケースで、AD型の使用を許可します）。これは、変数の `:datatype` 属性によって上書き可能です（これにより、変数はAD型を無視できます）。 `:datatype` は、Juliaの `DataType`（例：Float64）であるか、`eltypemap` で検索される文字列である可能性があります。

`allow_base_link==true` の場合、次のいずれかが真であれば、配列セット `arrays_idx` に新しい配列を割り当てるのではなく、ベース配列（`arrays_idx=1`）へのリンクが作成されます：     - 変数の要素型が `modeldata` のベースの要素型と一致する（arrays*idx=1）     - `use*base*transfer*jacobian=true`かつ 変数の`:transfer*jacobian`属性が設定されている     - 変数のフルネームが`use*base_vars` に含まれている

フィールドデータ型は、変数の `:field_data` 属性によって決定されます。これは、`host_dependent(v)==true` の変数に対して `default_host_dependent_field_data` のデフォルトを取ることができます（これらはターゲットまたはプロパティがリンクされていない変数で、ソルバーによって提供される外部依存関係を意図しています）。

`check_units_opt != :no` の場合、リンクされた変数の `:units` フィールドがチェックされ、結果として警告（`check_units_opt=:warn` の場合）またはエラー（`check_units_opt=:error` の場合）が発生します。
