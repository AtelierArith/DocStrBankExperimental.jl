```
expect2(::State, op_pairs)
```

与えられた演算子のペアの期待値をすべてのサイトで計算します。

# 例

```
expect2(state, (X, X))
expect2(state, [(X, Y), (X, Z), (Y, Z)])
...
```
