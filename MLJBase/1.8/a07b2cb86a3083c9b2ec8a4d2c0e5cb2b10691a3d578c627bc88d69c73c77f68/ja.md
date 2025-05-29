```
holdout = Holdout(; fraction_train=0.7, shuffle=nothing, rng=nothing)
```

`evaluate!`、`evaluate`、およびチューニングで使用するために、`Holdout` リサンプリング戦略をインスタンス化します。

```julia
train_test_pairs(holdout, rows)
```

`[(train, test)]` のペアを返します。ここで `train` と `test` はベクトルであり、`rows=vcat(train, test)` であり、`length(train)/length(rows)` はおおよそ `fraction_train` に等しくなります。

`rows` の事前シャッフルは `rng` と `shuffle` によって制御されます。`rng` が整数の場合、`Holdout` キーワードコンストラクタはそれを `MersenneTwister(rng)` にリセットします。それ以外の場合は、`AbstractRNG` オブジェクトが期待されます。

`rng` が指定されていない場合、`rng` は `Random.GLOBAL_RNG` にリセットされ、この場合、`shuffle=true` が指定されている場合にのみ行が事前にシャッフルされます。
