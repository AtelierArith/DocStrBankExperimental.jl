```
create(T::Type{<:AbstractDataTransformer}, driver::Symbol, source::String, dataset::DataSet;
       minpriority::Int=-100, maxpriority::Int=100)
```

新しい `T` を `source`/`dataset` から `driver` `driver` で作成します。

`driver` がシンボル `*` の場合、すべての可能なドライバーがチェックされ、最も高い優先度（`createpriority` に従って）の有効なドライバーが使用されます。優先度が `minpriority`–`maxpriority` の範囲外のドライバーは考慮されません。

作成されたデータトランスフォーマーが返されますが、指定された `driver` が無効な場合は、代わりに `nothing` が返されます。
