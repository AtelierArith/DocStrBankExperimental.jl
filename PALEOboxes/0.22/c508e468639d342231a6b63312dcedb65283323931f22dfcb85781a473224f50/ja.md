```
initialize_reactiondata!(model::Model, modeldata::AbstractModelData; kwargs...)
```

`ReactionMethods`からの`VarList_...`を処理し、`modeldata.sorted_methodsdata_...`を反応メソッドと対応する変数アクセサのソートされたリストで埋めます。

オプションで`create_dispatch_methodlists(model, modeldata, modeldata.cellranges_all)`を呼び出して、`modeldata.dispatchlists_all`をモデル全体のデフォルトの`ReactionMethodDispatchLists`に設定します。

# キーワード引数

  * `arrays_indices=1:num_arrays(modeldata)`：ディスパッチリストを生成するための`modeldata`の`arrays_idx`
  * `create_dispatchlists_all=false`：`modeldata.dispatchlists_all`を設定するためにtrue
  * `generated_dispatch=true`：`modeldata.dispatchlists_all`に自動生成されたコードを使用するためにtrue（高速ディスパッチ、遅いコンパイル）

```
