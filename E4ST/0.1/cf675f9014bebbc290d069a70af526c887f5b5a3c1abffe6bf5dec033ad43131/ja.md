```
E4ST.modify_model!(pol::EmissionPrice, config, data, model)
```

発電テーブルに、発電の排出率 * 排出価格としてのMWhあたりの値として排出価格を含む列を追加します。これを目的関数に`PerMWhGen`価格として追加し、[`add_obj_term!`](@ref)を使用します。
