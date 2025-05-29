```
partition2obs(part::Partition)
```

Partitionから最も可能性の高い状態を抽出し、便利な型に変換します。例えば、NucleotidePartitionはString型のヌクレオチド配列に変換されます。注意: 自分のPartition型に対してこの関数をオーバーロードする必要があります。
