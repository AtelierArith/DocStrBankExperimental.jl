```
ModelHierarchy(root_parts,model,num_procs_x_level)
```

  * `root_parts`: 初期コミュニケーター。サブコミュニケーターを生成するために使用されます。
  * `model`: 初期のリファイン可能な分散モデル。最も粗いレベルとして設定されます。
  * `num_procs_x_level`: 各レベルに分配したいプロセッサの数を含むベクター。`num_procs_x_level[end]`は`model`の部品の数と等しく、`num_procs_x_level[1]`は`root_parts`の利用可能なプロセッサの総数よりも少なくする必要があります。
