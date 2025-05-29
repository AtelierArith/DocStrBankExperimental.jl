```
optimaltransportation(M::AbstractArray;
        [a, b, λ=1, ϵ=1e-10, maxiter=100])
```

生態ネットワークにおける最適輸送を実行します。ここで、`M`はユーティリティ行列として扱われ、2つの栄養レベルの種が相互作用する際の好みを定量化します。`a`（行の合計、上位種に対応）および/または`b`（列の合計、下位種に対応）を指定することで、両方、一方、またはどちらの種の個体数も固定できます。エントロピー正則化の強さは`λ`によって設定され、高い値はより多くのユーティリティを示し、低い値はより多くのエントロピーを示します。

ϵと`maxiter`はSinkhorn反復の回数を制御します。これらを変更する必要はないでしょう。

このバージョンは配列で動作します。

Stock, M., Poisot, T., & De Baets, B. (2021). « Optimal transportation theory for species interaction networks. » Ecology and Evolution, 00(1), ece3.7254. https://doi.org/10.1002/ece3.7254
