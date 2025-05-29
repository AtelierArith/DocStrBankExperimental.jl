```
DataFreeTree(treetype, data[, reorderbufffer = similar(data), kwargs...]) -> datafreetree
```

`DataFreeTree`を作成します。これは`KDTree`または`BallTree`をラップします。キーワード引数はそれぞれのコンストラクタに渡されます。

`KDTree`または`BallTree`は、基になるデータへの参照なしで保存されます。使用する前に、`injectdata`を使用してデータ配列に再リンクする必要があります。
