```
splitdata(x, ratio)
```

データセット `x` をランダムに2つのデータセット `x1` と `x2` に分割します。`x2` のサンプルの割合は、指定された `ratio` に等しい（またはできるだけ近い）ようになります。

# 例:

```
trainingdata, testdata = splitdata(data, 0.1) # テストデータとして10%を使用
```
