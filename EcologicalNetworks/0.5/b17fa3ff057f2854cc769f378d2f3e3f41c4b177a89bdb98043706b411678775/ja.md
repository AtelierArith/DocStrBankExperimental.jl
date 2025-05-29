```
AJS(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: UnipartiteNetwork}
```

ネットワーク内の種のペアに対する加法的ジャッカード類似度（AJS）。AJSは0（共通の種なし）から1（同じプロファイル）までの範囲で変動します。この関数は、`dims`引数を使用して、後継者または前任者のみに基づいてAJSを測定するために使用できます。

この関数は、類似性を測定するためにすべての*直接的*な捕食者と被食者を使用することに注意してください（したがって、即時の隣接者を超えることはありません）。

#### 参考文献

Gao, P., Kupfer, J.A., 2015. Uncovering food web structure using a novel trophic similarity measure. Ecological Informatics 30, 110–118. https://doi.org/10.1016/j.ecoinf.2015.09.013
