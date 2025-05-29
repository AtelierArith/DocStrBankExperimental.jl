```
Xs = source(X=nothing)
```

学習ネットワーク `Source` オブジェクトを定義し、いくつかの入力データ `X` をラップします。これは、ネットワークをスタンドアロンモデルとしてエクスポートする目的で `nothing` であることができます。エクスポートされていないネットワークのトレーニングとテストには、適切なベクトル、テーブル、またはその他のデータコンテナが期待されます。

`Source` オブジェクトの呼び出し動作は次のとおりです：

```julia
Xs() = X
Xs(rows=r) = selectrows(X, r)  # 例: X[r,:] は DataFrame の場合
Xs(Xnew) = Xnew
```

参照： [`MLJBase.prefit`](@ref), [`sources`](@ref), [`origins`](@ref), [`node`](@ref).
