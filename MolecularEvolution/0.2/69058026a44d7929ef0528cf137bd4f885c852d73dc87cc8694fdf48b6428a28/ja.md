```
combine!(dest::P, src::P) where P<:Partition
```

同じタイプの2つのパーティションからの証拠を結合し、結果をdestに格納します。注意: 自分のPartitionタイプに対してこれをオーバーロードする必要があります。
