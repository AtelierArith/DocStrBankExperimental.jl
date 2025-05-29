```
hchebinterp(f, a, b, [criterion=SpectralError()]; order=defaultorder(criterion), atol=0, rtol=0, norm=norm, maxevals=typemax(Int), initdiv=1, reuse=true)
```

区間 $[a,b]$ での `f` の区分多項式補間を、要求された許容誤差に対して点ごとに正確な次数 `order` のものとして返します。`criterion::AbstractAdaptCriterion` を使用して h-適応のための補間誤差を推定します。デフォルトでは、`SpectralError()` の `order` は 15 で、`HAdaptError()` の場合は 4 です。

!!! note "HChebInterp 1.1"
    `reuse` キーワードは少なくとも HChebInterp v1.1 が必要です。


キーワード `reuse` は、可能な限り補間グリッド上で関数評価を再利用することをアルゴリズムに指示します。高コストの関数や数秒単位の補間問題においては、その利点が顕著であり、デフォルトのソルバーでは関数評価の約 12% の節約が見込まれます。補間点の検索が必ずしも速いわけではないため、`reuse=false` を設定してこの最適化を無効にすることができます。
