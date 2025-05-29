```
allocate_variables!(domain, modeldata, arrays_idx; [hostdep=false] [, kwargs...])
```

ドメイン変数のメモリを割り当てます。

`hostdep=false`の場合、内部変数のみが割り当てられ、ホスト依存変数（通常は状態変数および導関数 + いかなる外部依存関係）をホスト管理配列のビューに設定できるようになります。

[`allocate_variables!(vars, modeldata::AbstractModelData, arrays_idx::Int)`](@ref)を参照してください。
