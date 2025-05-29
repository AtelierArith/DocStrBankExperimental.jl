```
manage_ssmc(; sort_by::Symbol=:name, rev::Bool=false)
```

ユーザーがSuiteSparseMatrixCollectionから行列を選択的に削除できるプロンプトを開きます。

デフォルトでは、行列は名前でソートされます。代わりに、`sort_by=:size`を指定することで、ディスク上のファイルサイズでソートできます。`rev=true`を使用すると、ソート順を逆にできます。
