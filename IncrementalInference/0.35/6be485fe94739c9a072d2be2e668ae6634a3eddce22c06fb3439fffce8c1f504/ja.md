```julia
shrinkFactorGraph(fg; upto)

```

ファクターグラフを剪定して、最大 `upto` 個の変数を保持します。

警告: `isSolvable()` など、IncrementalInference の外にある関数を使用するため、別の場所に配置する必要があるでしょう。
