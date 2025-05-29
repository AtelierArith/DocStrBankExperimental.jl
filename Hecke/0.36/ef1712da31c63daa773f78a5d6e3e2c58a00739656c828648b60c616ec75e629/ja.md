```
direct_sum(x::Vararg{T}) where T <: AbstractLat -> T, Vector{AbstractSpaceMor}
direct_sum(x::Vector{T}) where T <: AbstractLat -> T, Vector{AbstractSpaceMor}
```

与えられた二次またはエルミート格子のコレクション $L_1, \ldots, L_n$ に対して、それらの直和 $L := L_1 \oplus \ldots \oplus L_n$ を返し、対応する環境空間間の写像として見られる注入 $L_i \to L$ を返します。

`AbstractLat` 型のオブジェクトの場合、有限直和と有限直積は一致し、したがって双積と呼ばれます。`L` を直積として得たい場合は、射影 $L \to L_i$ を伴う `direct_product(x)` を呼び出す必要があります。`L` を注入 $L_i \to L$ と射影 $L \to L_i$ を伴う双積として得たい場合は、`biproduct(x)` を呼び出す必要があります。
