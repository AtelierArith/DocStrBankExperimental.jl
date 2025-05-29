```
setrange(chains::Chains, range::AbstractVector{Int})
```

`chains`から`range`でインデックス付けされたイテレーションを持つ新しいチェーンを生成します。

新しいチェーンと`chains`は、メモリ内で同じデータを共有します。
