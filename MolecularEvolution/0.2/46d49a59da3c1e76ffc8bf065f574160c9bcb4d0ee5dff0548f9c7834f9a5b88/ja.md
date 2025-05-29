```
node_samples(tree; partition_inds = 1)
```

ツリーの各ノード（内部ノードやルートを含む）に対する `partition2obs` の結果を返します。これは、`sample_down!` が呼び出された後に使用できます。例えば、コドンモデルを使用している場合、これは各ノードのCodonPartitionから文字列を抽出します。デフォルトでは最初のパーティションに作用しますが、`partition_inds` を設定することで変更できます。`partition_inds` はインデックスのベクトルでもあり、その場合、結果は各ノードに対するベクトルになります。
