```
make_vector_fold(pattern, gap, fold, kind = :mutable)
```

折りたたまれたベクターを構築するためのディスパッチャーです。ベクターの`kind`は、`:mutable`（デフォルト）または`:immutable`のいずれかに設定できます。デフォルトはほとんどの場合で高速ですが、`pattern`、`gap`、および`fold`パラメータに依存します。重要なコードの場合は、両方のオプションをベンチマークすることをお勧めします。
