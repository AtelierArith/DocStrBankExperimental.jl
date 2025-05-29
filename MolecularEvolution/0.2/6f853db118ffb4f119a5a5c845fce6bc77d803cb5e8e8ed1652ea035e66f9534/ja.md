```
leaf_samples(tree; partition_inds = 1)
```

木の各葉に対する `partition2obs` の結果を返します。例えば、`sample_down!` が呼ばれた後に使用できます。例えばコドンモデルを使用している場合、これは各葉のCodonPartitionから文字列を抽出します。デフォルトでは最初のパーティションに作用しますが、`partition_inds` を設定することで変更できます。`partition_inds` はインデックスのベクターでもあり、その場合、結果は各葉に対するベクターになります。
