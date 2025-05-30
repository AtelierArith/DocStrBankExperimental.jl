```
sample([rng], wv::AbstractWeights)
```

`wv`に与えられた重みに比例して、`1:length(wv)`の中から単一のランダム整数を選択します。

オプションで、最初の引数として乱数生成器`rng`を指定できます（デフォルトは`Random.GLOBAL_RNG`です）。
