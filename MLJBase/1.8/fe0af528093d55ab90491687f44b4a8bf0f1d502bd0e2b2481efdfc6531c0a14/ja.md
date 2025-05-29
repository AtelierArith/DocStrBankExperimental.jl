```
stratified_cv = StratifiedCV(; nfolds=6,
                               shuffle=false,
                               rng=Random.GLOBAL_RNG)
```

層化交差検証のリサンプリング戦略で、`evaluate!`、`evaluate`、およびチューニングで使用します。分類問題（`OrderedFactor`または`Multiclass`ターゲット）のみ適用されます。

```julia
train_test_pairs(stratified_cv, rows, y)
```

`nfolds`の長さのイテレータを返し、各`train`と`test`は`rows`のサブベクターの`(train, test)`ペアです。`test`ベクターは相互に排他的で、`rows`を使い果たします。各`train`ベクターは、対応する`test`ベクターの補集合です。

通常の交差検証とは異なり、各`train`および`test`に対応するターゲット`y`のレベルの分布は、可能な限り`y[rows]`全体のそれを再現するように制約されています。

層化`train_test_pairs`アルゴリズムは、ラベルの名前変更に対して不変です。たとえば、`replace!(y, 'a' => 'b', 'b' => 'a')`を実行し、その後`train_test_pairs`を再実行すると、返される`(train, test)`ペアは同じになります。

`rows`の事前シャッフルは、`rng`と`shuffle`によって制御されます。`rng`が整数の場合、`StratifedCV`キーワードコンストラクタはそれを`MersenneTwister(rng)`にリセットします。それ以外の場合は、いくつかの`AbstractRNG`オブジェクトが期待されます。

`rng`が指定されていない場合、`rng`は`Random.GLOBAL_RNG`にリセットされ、この場合、`shuffle=true`が明示的に指定されている場合にのみ、行は事前にシャッフルされます。
