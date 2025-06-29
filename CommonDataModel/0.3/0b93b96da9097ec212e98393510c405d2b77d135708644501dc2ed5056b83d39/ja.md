```
write(dest::AbstractDataset, src::AbstractDataset; include = keys(src), exclude = [])
```

`src` データセットの変数を空の `dest` データセットに書き込みます（`dest` は `"a"` または `"c"` モードで開かれている必要があります）。キーワード `include` と `exclude` は、`src` のどの変数を含めるべきか（デフォルトではすべて）、またはどの変数を除外すべきか（デフォルトではなし）を設定します。

最初の引数がファイル名の場合、データセットは作成モード（`"c"`）で開かれます。

この関数は、マルチファイルデータセットからデータセットを保存したいときに便利です。

サブセットを保存するには、`view` 関数を使用してデータセットを仮想的にスライスできます：

## 例

```
NCDataset(fname_src) do ds
    write(fname_slice,view(ds, lon = 2:3))
end
```

ソースファイル `fname_src` のすべての変数は、`lon` 次元に沿ってインデックス `2:3` でスライスされます。すべての属性（および次元 `lon` を持たない変数）は、変更されることなくコピーされます。
