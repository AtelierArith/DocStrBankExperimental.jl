```
dag(T::ITensor; allow_alias = true)
```

ITensor `T` の要素を複素共役し、インデックスをダガーします。

デフォルトでは、ITensorのエイリアスが返されます（すなわち、出力ITensorは入力ITensorとデータを共有する可能性があります）。`allow_alias = false` の場合、エイリアスは決して返されません。
