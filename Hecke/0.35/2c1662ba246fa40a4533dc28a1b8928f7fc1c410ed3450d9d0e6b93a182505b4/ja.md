```
direct_product(x::Vararg{T}) where T <: AbstractLat -> T, Vector{AbstractSpaceMor}
direct_product(x::Vector{T}) where T <: AbstractLat -> T, Vector{AbstractSpaceMor}
```

与えられた二次またはエルミート格子のコレクション $L_1, \ldots, L_n$ に対して、それらの直積 $L := L_1 \times \ldots \times L_n$ を返し、対応する周囲空間間の写像として見た射影 $L \to L_i$ も返します。

`AbstractLat` 型のオブジェクトに対して、有限直和と有限直積は一致し、したがってそれらは双積と呼ばれます。もし `L` を注入 $L_i \to L$ を伴う直和として得たい場合は、`direct_sum(x)` を呼び出すべきです。もし `L` を注入 $L_i \to L$ と射影 $L \to L_i$ を伴う双積として得たい場合は、`biproduct(x)` を呼び出すべきです。
