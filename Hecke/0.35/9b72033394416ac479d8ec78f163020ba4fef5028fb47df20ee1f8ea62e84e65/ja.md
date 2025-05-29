```
direct_product(x::Vararg{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}
direct_product(x::Vector{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}
```

$$
\mathbb Z
$$

-格 $L_1, \ldots, L_n$ のコレクションが与えられたとき、それらの直積 $L := L_1 \times \ldots \times L_n$ を返し、射影 $L \to L_i$ を返します。（対応する環境空間間の写像として見なされます）。

`ZZLat` 型のオブジェクトに対して、有限直和と有限直積は一致し、それらは双積と呼ばれます。`L` を注入 $L_i \to L$ を伴う直和として取得したい場合は、`direct_sum(x)` を呼び出すべきです。`L` を注入 $L_i \to L$ と射影 $L \to L_i$ を伴う双積として取得したい場合は、`biproduct(x)` を呼び出すべきです。
