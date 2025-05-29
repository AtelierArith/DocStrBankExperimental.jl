```
solve_MVR(Σ::AbstractMatrix)
```

固定XおよびモデルXノックオフに対する最小分散ベースの再構成可能性問題を相関行列Σに対して解決します。ユーザーはこの関数の代わりに`solve_s`を呼び出すべきです。

「再構成可能性の最小化による強力なノックオフ」Spector、Asher、Lucas Janson（2020）のアルゴリズム1を参照してください https://arxiv.org/pdf/2011.14625.pdf
