```
CategoricalLikelihood(l=BijectiveSimplexLink(softmax))
```

カテゴリカル尤度は、データに関連する不確実性が[Categorical分布](https://en.wikipedia.org/wiki/Categorical_distribution)に従うと仮定する場合に使用されます。

`n` カテゴリを持つ分布を仮定すると：

## `n-1` 入力 (双射リンク)

双射変換を使用することができ、リンク（例えば `softmax`）を[`BijectiveSimplexLink`](@ref)でラップすることで、`n-1` 入力のみが必要です：

$$
    p(y|f_1, f_2, \dots, f_{n-1}) = \operatorname{Categorical}(y | l(f_1, f_2, \dots, f_{n-1}, 0))
$$

デフォルトのコンストラクタは `softmax` の周りの双射リンクです。

## `n` 入力 (非双射リンク)

`0` を連結せずに直接入力を渡すこともできます：

$$
    p(y|f_1, f_2, \dots, f_n) = \operatorname{Categorical}(y | l(f_1, f_2, \dots, f_n))
$$

このバリアントは過剰パラメータ化されており、`n` 次元のパラメータ空間に `n-1` の独立したパラメータが埋め込まれています。詳細については、この[ウィキペディアのリンク](https://en.wikipedia.org/wiki/Exponential_family#Table_of_distributions)のセクションの最後を参照してください。これはバリアント1と2に対応しています。
