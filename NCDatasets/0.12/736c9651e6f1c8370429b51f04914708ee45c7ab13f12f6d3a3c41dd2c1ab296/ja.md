```
write(dest_filename::AbstractString, src::AbstractNCDataset; include = keys(src), exclude = [], idimensions = Dict())
write(dest::NCDataset, src::AbstractNCDataset; include = keys(src), exclude = [], idimensions = Dict())
```

`src` データセットの変数を空の `dest` データセットに書き込みます（`dest` は `"a"` または `"c"` モードで開かれている必要があります）。キーワード `include` と `exclude` は、`src` のどの変数を含めるか（デフォルトではすべて）、またはどの変数を除外するか（デフォルトではなし）を設定します。

最初の引数がファイル名の場合、データセットは作成モード（`"c"`）で開かれます。

この関数は、マルチファイルデータセットからデータセットを保存したいときに便利です。

`idimensions` は、データセットの一部のみを保存する必要がある場合に、次元名をインデックスのリストにマッピングする辞書です。

## 例

```
NCDataset(fname_src) do ds
    write(fname_slice,ds,idimensions = Dict("lon" => 2:3))
end
```

次元 `lon` を持つソースファイル `fname_src` のすべての変数は、`lon` 次元のインデックス `2:3` に沿ってスライスされます。すべての属性（および次元 `lon` を持たない変数）は、変更されずにコピーされます。

出力ファイルのすべての変数はメモリにロードできると仮定されています。
