```
savedataset(datasetpath, md; instance_ids, name, force = false)
```

`md` AbstractMultiDatasetを`datasetpath`のディスクに次の形式で保存します：

datasetpath     ├─ Example*1     │     └─ Modality*1.csv     │     └─ Modality*2.csv     │     └─ ...     │     └─ Modality*n.csv     │     └─ Metadata.txt     ├─ Example*2     │     └─ Modality*1.csv     │     └─ Modality*2.csv     │     └─ ...     │     └─ Modality*n.csv     │     └─ Metadata.txt     ├─ ...     ├─ Example_n     ├─ Metadata.txt     └─ Labels.csv

# 引数

  * `instance_ids`はインスタンスの識別子を示す`AbstractVector{Integer}`です。
  * `name`は`AbstractString`で、データセットの名前を示し、データセットのメタデータに保存されます。
  * `force`は`Bool`で、`true`に設定されている場合、`datasetpath`がすでに存在する場合は上書きされ、それ以外の場合は操作が中止されます。（デフォルト = `false`）
  * `labels_indices`は`AbstractVector{Integer}`で、ラベルの列のインデックスを含みます（MultiDatasetを渡す場合のみ許可されます）。

`AbstractMultiDataset`の代わりに、`DataFrame`を第二引数として渡すことができます。この場合、データセットの`grouped_variables`を表す第三の位置引数が必要です。`grouped_variables`の構文については[`MultiDataset`](@ref)を参照してください。
