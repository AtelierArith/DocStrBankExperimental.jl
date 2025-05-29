```
splitobs(data, [at = 0.7], [obsdim]) -> Tuple
```

`data`を`at`の値に比例して複数のサブセットに分割します。

この関数は静的に分割を行い、ランダム化は行いません。この関数は、最初のN-1の要素/サブセットに`at`で指定された`data`の観測値の割合を含むデータサブセットの`NTuple`を作成します。

例えば、`at`が`Float64`の場合、返り値は2つの要素（すなわちサブセット）を持つタプルとなり、最初の要素には`at`で指定された観測値の割合が含まれ、2番目の要素には残りが含まれます。以下のコードでは、最初のサブセット`train`が観測値の最初の70%を含み、2番目のサブセット`test`が残りを含みます。

```julia
train, test = splitobs(X, at = 0.7)
```

`at`が`Float64`のタプルである場合、追加のサブセットが作成されます。この例では、`train`が観測値の最初の50%を持ち、`val`が次の30%、`test`が最後の20%を持ちます。

```julia
train, val, test = splitobs(X, at = (0.5, 0.3))
```

複数のデータ引数をタプルとして`splitobs`を呼び出すことも可能で、すべての引数は同じ数の観測値を持つ必要があります。これはラベル付きデータに便利です。

```julia
train, test = splitobs((X, y), at = 0.7)
(x_train,y_train), (x_test,y_test) = splitobs((X, y), at = 0.7)
```

観測値をサブセットにランダムに割り当てる必要がある場合は、`shuffleobs`と組み合わせて使用できます。

```julia
# 今回は観測値がランダムに割り当てられます。
train, test = splitobs(shuffleobs((X,y)), at = 0.7)
```

配列を扱う際には、どの次元が観測値を表すかを選択したい場合があります。デフォルトでは最後の次元が仮定されますが、これを上書きすることができます。

```julia
# ここでは各行が観測値を表すと言っています
train, test = splitobs(X, obsdim = 1)
```

関数は型安定なAPIも提供します。

```julia
# キーワード引数を避けることで、コンパイラは返り値の型を推論できます
train, test = splitobs((X,y), 0.7)
train, test = splitobs((X,y), 0.7, ObsDim.First())
```

データサブセットに関する詳細は[`DataSubset`](@ref)を参照してください。

ターゲット分布を保持する関連関数については[`stratifiedobs`](@ref)を参照してください。
