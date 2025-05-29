```
cv = CV(; nfolds=6,  shuffle=nothing, rng=nothing)
```

交差検証のリサンプリング戦略で、`evaluate!`、`evaluate`、およびチューニングで使用します。

```julia
train_test_pairs(cv, rows)
```

`nfolds`の長さのイテレータを返し、各`train`と`test`は`rows`のサブベクター（行インデックス）のペアです。`test`ベクターは相互に排他的で、`rows`を完全に使い果たします。各`train`ベクターは対応する`test`ベクターの補集合です。行の事前シャッフルがない場合、`rows`の順序は保持され、`rows`は生成された順序で`test`ベクターの連結と正確に一致します。最初の`r`個のテストベクターは長さ`n + 1`を持ち、ここで`n, r = divrem(length(rows), nfolds)`、残りのテストベクターは長さ`n`を持ちます。

`rows`の事前シャッフルは`rng`と`shuffle`によって制御されます。`rng`が整数の場合、`CV`キーワードコンストラクタはそれを`MersenneTwister(rng)`にリセットします。それ以外の場合は、いくつかの`AbstractRNG`オブジェクトが期待されます。

`rng`が指定されていない場合、`rng`は`Random.GLOBAL_RNG`にリセットされ、この場合、`shuffle=true`が明示的に指定されない限り、行は事前にシャッフルされません。
