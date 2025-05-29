```
minimum_weight_perfect_matching(g, w::Dict{Edge,Real})
minimum_weight_perfect_matching(g, w::Dict{Edge,Real}, cutoff)
```

グラフ `g` とエッジに関連付けられた重みを含むエッジマップ `w` が与えられたとき、正確に `nv(g)/2` エッジを含むものの中で最小の合計重みを持つマッチングを返します。

`g` の中で `w` に存在しないエッジはマッチングの対象として考慮されません。

この関数は、Kolmogorov の BlossomV アルゴリズムの Julia ラッパーである BlossomV.jl パッケージに依存しています。

最終的に、計算時間を短縮するために、カットオフよりも重みが高いエッジを除外する `cutoff` 引数を指定することができます。

返されるオブジェクトは `MatchingResult` 型です。

エラーが発生した場合は、オプション引数 `tmaxscale` （デフォルトは `tmaxscale=10`）を変更してみてください。
