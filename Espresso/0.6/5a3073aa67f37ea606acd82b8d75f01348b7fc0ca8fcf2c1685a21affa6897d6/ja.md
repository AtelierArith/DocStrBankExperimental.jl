可能性のあるインデックス付き変数を名前とインデックスに分割します。例：

```
split_indexed(:x)         ==> (:x, [])
split_indexed(:(x[i,j]))  ==> (:x, [:i,:j])
```

また、make_indexedも参照してください。
