```
MultinomialPolya
```

線形予測子を通じてソフトマックスを用いたMultinomialPolya尤度を表すノードタイプ。重みに対してノーマル事前分布が使用されます。事前分布は、過分散を持つカウントデータのモデリングに使用されるPolyaGamma分布で拡張されます。この実装は、ベイズ推論のためのPolyaGamma拡張スキームに従っています。Multinomial回帰に使用できます。デフォルトで21ポイントのPolyaGamma拡張スキームに対してキュバチュア積分を使用します。キュバチュアポイントの数を変更するには`MultinomialPolyaMeta`を使用してください。
