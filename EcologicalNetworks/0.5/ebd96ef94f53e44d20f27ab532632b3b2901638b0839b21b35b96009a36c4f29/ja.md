```
EAJS(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: UnipartiteNetwork}
```

ネットワーク内の種のペアに対する拡張加法ジャッカード類似度（AJS）。AJSは0（共通の種なし）から1（同じプロファイル）までの範囲で変動します。この関数は、`dims`引数を使用して、後継者または前任者のみに基づいてAJSを測定するために使用できます。

この関数は、種の近隣を定義するために、距離50までのすべての相互作用をカウントすることに注意してください。これは、ほとんどの生態系ネットワークにとって十分であるはずです。

#### 参考文献

Gao, P., Kupfer, J.A., 2015. Uncovering food web structure using a novel trophic similarity measure. Ecological Informatics 30, 110–118. https://doi.org/10.1016/j.ecoinf.2015.09.013
