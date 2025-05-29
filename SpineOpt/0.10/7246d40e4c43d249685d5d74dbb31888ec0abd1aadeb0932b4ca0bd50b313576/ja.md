```
active_stochastic_paths(
    m; stochastic_structure::Union{Object,Vector{Object}}, t::Union{TimeSlice,Vector{TimeSlice}}
)
```

`Array` の確率的パスであり、各パスは `stochastic_scenario` `Object` の `Array` です。

パスは次のように取得されます。

1. モデル `m` に関連付けられた確率的 DAG から始めます。
2. 指定された `stochastic_structure` に含まれないすべてのシナリオを削除します。
3. 指定された `t` と重ならないシナリオを削除します。
4. 残りのサブ DAG でルートからリーフまでのすべてのパスを返します。
