```
kfolds(data, k = 5)
```

`data` コンテナを `k` 回、`k` フォールド戦略を使用して再分割し、フォールドのシーケンスを遅延イテレータとして返します。実際のデータがコピーされるのは [`getobs`](@ref) が呼び出されるまでであり、データのサブセットのみが作成されます。

概念的には、k-フォールド再分割戦略は、与えられた `data` を `k` 個のほぼ同じサイズの部分に分割します。各部分は一度検証セットとして使用され、残りの部分はトレーニングに使用されます。これにより、`data` の `k` 個の異なるパーティションが生成されます。

データセットのサイズが指定された `k` で割り切れない場合、残りの観測値は部分間で均等に分配されます。

```julia
for (x_train, x_val) in kfolds(X, k=10)
    # 10 回呼び出されるコード
    # numobs(x_val) は反復ごとに ±1 まで異なる場合があります
end
```

複数の変数がサポートされています（例：ラベル付きデータの場合）

```julia
for ((x_train, y_train), val) in kfolds((X, Y), k=10)
    # ...
end
```

デフォルトでは、フォールドは静的分割を使用して作成されます。観測値をフォールドにランダムに割り当てるには [`shuffleobs`](@ref) を使用します。

```julia
for (x_train, x_val) in kfolds(shuffleobs(X), k=10)
    # ...
end
```

関連する関数については [`leavepout`](@ref) を参照してください。
