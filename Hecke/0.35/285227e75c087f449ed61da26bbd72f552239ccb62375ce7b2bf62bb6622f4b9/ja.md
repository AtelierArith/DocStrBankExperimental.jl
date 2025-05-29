```
biproduct(x::Vararg{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
biproduct(x::Vector{ZZLat}) -> ZZLat, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
```

$$
\mathbb Z
$$

-格 $L_1, \ldots, L_n$ のコレクションが与えられたとき、それらのバイプロダクト $L := L_1 \oplus \ldots \oplus L_n$ を返し、注入 $L_i \to L$ と射影 $L \to L_i$ を返します。（対応する環境空間間の写像として見なされます）。

`ZZLat` 型のオブジェクトに対して、有限直和と有限直積は一致し、したがってバイプロダクトと呼ばれます。注入 $L_i \to L$ を伴う直和として `L` を取得したい場合は、`direct_sum(x)` を呼び出す必要があります。射影 $L \to L_i$ を伴う直積として `L` を取得したい場合は、`direct_product(x)` を呼び出す必要があります。
