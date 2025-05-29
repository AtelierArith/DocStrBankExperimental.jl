インデックス付き変数を作成します。例：

```
make_indexed(:x, [])       ==> :x
make_indexed(:x, [:i,:j])  ==> :(x[i,j])
```

他にも、split_indexedがあります。
