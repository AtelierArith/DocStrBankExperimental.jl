```
biproduct(x::Vararg{T}) where T <: AbstractLat -> T, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
biproduct(x::Vector{T}) where T <: AbstractLat -> T, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
```

与えられた二次またはエルミート格子のコレクション $L_1, \ldots, L_n$ に対して、それらのバイプロダクト $L := L_1 \oplus \ldots \oplus L_n$ を返し、注入 $L_i \to L$ と射影 $L \to L_i$ （対応する周囲空間間の写像として見られる）を返します。

`AbstractLat` 型のオブジェクトに対して、有限直和と有限直積は一致し、したがってバイプロダクトと呼ばれます。注入 $L_i \to L$ を伴う直和として `L` を取得したい場合は、`direct_sum(x)` を呼び出す必要があります。射影 $L \to L_i$ を伴う直積として `L` を取得したい場合は、`direct_product(x)` を呼び出す必要があります。
