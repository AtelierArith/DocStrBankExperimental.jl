```
VariableAggregatorNamed(modeldata, arrays_idx=1) -> VariableAggregatorNamed
VariableAggregatorNamed(vars, modeldata, arrays_idx=1) -> VariableAggregatorNamed
VariableAggregatorNamed(va::VariableAggregator; ignore_cellranges=false) -> VariableAggregatorNamed
```

VariableDomainsをネストされたNamedTuplesに集約し、DomainおよびVariable名をキー、データ配列（`get_data`から）を値として使用します。

Variable名に含まれる`/`文字は`__`（ダブルアンダースコア）に置き換えられます。

これにより、名前による変数への直接アクセスが可能になり、主にテストや小規模モデルに役立ちます。

# フィールド

  * `vars`: VariableDomainsのネストされたNamedTuples（domainname, varname）
  * `values`: データ配列のネストされたNamedTuples（domainname, varname）。
