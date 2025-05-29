```
sample([rng], a::AbstractArray, [wv::AbstractWeights])
```

配列 `a` の単一のランダム要素を選択します。サンプリング確率は、提供された場合は `wv` に与えられた重みに比例します。

オプションで、最初の引数として乱数生成器 `rng` を指定できます（デフォルトは `Random.default_rng()` です）。
