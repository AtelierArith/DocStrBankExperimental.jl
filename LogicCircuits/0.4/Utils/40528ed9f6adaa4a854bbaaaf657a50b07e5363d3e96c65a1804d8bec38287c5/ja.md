Xの補完値を返します（別のDataFrameからの統計を使用する可能性があります）

例えば、同じDataFrameを使用して補完するには：

```
impute(X; method=:median)
```

別のDataFrameを使用して補完統計を提供したい場合：

```
impute(test_x, train_x; method=:mean)
```

サポートされているメソッドは`:median`、`:mean`、`:one`、`:zero`です。
