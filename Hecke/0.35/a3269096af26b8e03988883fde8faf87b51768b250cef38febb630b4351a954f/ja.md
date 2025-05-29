```
direct_product(x::Vararg{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
direct_product(x::Vector{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
```

与えられた二次元またはエルミート空間のコレクション $V_1, \ldots, V_n$ に対して、それらの直積 $V := V_1 \times \ldots \times V_n$ を返し、射影 $V \to V_i$ を返します。

`AbstractSpace` 型のオブジェクトの場合、有限直和と有限直積は一致し、したがって双積と呼ばれます。もし `V` を注入 $V_i \to V$ を伴う直和として得たい場合は、`direct_sum(x)` を呼び出すべきです。もし `V` を注入 $V_i \to V$ と射影 $V \to V_i$ を伴う双積として得たい場合は、`biproduct(x)` を呼び出すべきです。
