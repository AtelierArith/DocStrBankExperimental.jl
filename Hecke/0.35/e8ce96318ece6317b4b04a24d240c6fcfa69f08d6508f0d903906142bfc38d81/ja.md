```
direct_sum(x::Vararg{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}
direct_sum(x::Vector{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}
```

$$
\mathbb Z
$$

-格子 $L_1, \ldots, L_n$ のコレクションが与えられたとき、それらの直和 $L := L_1 \oplus \ldots \oplus L_n$ を返し、注入 $L_i \to L$ も返します。（対応する周囲空間間の写像として見なされます）。

`ZZLat` 型のオブジェクトに対して、有限直和と有限直積は一致し、それらは双積と呼ばれます。`L` を直積として得たい場合は、射影 $L \to L_i$ を伴って `direct_product(x)` を呼び出すべきです。`L` を注入 $L_i \to L$ と射影 $L \to L_i$ を伴う双積として得たい場合は、`biproduct(x)` を呼び出すべきです。
