```
Genotype::DataType
```

便宜上、`NTuple{N, <:Signed} where N`のエイリアスであり、PopDataにおける個々の遺伝子型を記述する型です。具体的には、`SNP`は`NTuple{N, Int8}`のエイリアスであり、`MSat`は`NTuple{N, Int16}`のエイリアスです。
