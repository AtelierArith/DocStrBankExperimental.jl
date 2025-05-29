AbstractModelはあなたのモデルの基本タイプです。モデルを手動でインスタンス化するべきではありません。

次の方法で取得できます：

  * クエリ: `db[MyModel[conditions...]][idx]`
  * 挿入: `MyModel(db)(kwargs)`
  * 更新: `newmodel = db[oldmodel](update_kwargs...)` または `@update db[model] key1=val1 key2=val2 ...`
